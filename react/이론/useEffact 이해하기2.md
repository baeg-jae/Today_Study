```js
<!DOCTYPE html>
<html lang="en">
  <body>
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <div id="root"></div>
    <script type="text/babel">
      const rootElement = document.getElementById("root");

      const Child = () => {
        console.log("   Child render start");
        const [text, setText] = React.useState(() => {
          console.log("   Child useState");
          return "";
        });
        React.useEffect(() => {
          console.log("   Child useEffect, no deps");
          return () => {
            console.log("   Child useEffect [Cleanup], no deps");
          };
        });
        React.useEffect(() => {
          console.log("   Child useEffect, empty deps");
          return () => {
            console.log("   Child useEffect [Cleanup], empty deps");
          };
        }, []);
        React.useEffect(() => {
          console.log("   Child useEffect, [text] deps");
          return () => {
            console.log("   Child useEffect [Cleanup], [text] deps");
          };
        }, [text]);

        function handleChange(event) {
          setText(event.target.value);
        }
        const element = (
          <>
            <input onChange={handleChange} />
            <p>{text}</p>
          </>
        );
        console.log("   Child render end");
        return element;
      };
      const App = () => {
        console.log("App render start");
        const [show, setShow] = React.useState(() => {
          console.log("App useState");
          return false;
        });

        React.useEffect(() => {
          console.log("App useEffect, no deps");
          return () => {
            console.log("App useEffect [Cleanup], no deps");
          };
        });
        //deps가 없으면 모든 것에 호출됨
        React.useEffect(() => {
          console.log("App useEffect, empty deps");
          return () => {
            console.log("App useEffect [Cleanup], empty deps");
          };
        }, []);
        //처음에 랜더될때문 반응
        React.useEffect(() => {
          console.log("App useEffect, [show]");
          return () => {
            console.log("App useEffect [Cleanup], [show]");
          };
        }, [show]);
        //값이 바뀔때만 반응

        function handleClick() {
          setShow((prev) => !prev);
        }

        console.log("App render end");
        return (
          <>
            <button onClick={handleClick}>Search</button>
            {show ? <Child /> : null}
          </>
        );
      };

      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>
```
```
여기서 useEffect에 Cleanup 기능을 추가하여 사용해보겠다.
이럴경우 순서가 많이 바뀐다. 

update시 useEffect cleanup이 먼저 실행되고 useEffect가 실행된다.
dependency array는 전달받은 값의 변화 있는 경우에만 실행된다.
```
