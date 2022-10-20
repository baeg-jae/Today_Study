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
        });
        React.useEffect(() => {
          console.log("   Child useEffect, empty deps");
        }, []);
        React.useEffect(() => {
          console.log("   Child useEffect, [text] deps");
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
        });
        //deps가 없으면 모든 것에 호출됨
        React.useEffect(() => {
          console.log("App useEffect, empty deps");
        }, []);
        //처음에 랜더될때문 반응
        React.useEffect(() => {
          console.log("App useEffect, [show]");
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
버튼을 눌렀을때 <Child/> 기능이 실행되는데
이때 Child useEffact가 먼저 실행되고
그후 App useEffact가 실행된다.

이 원리가 중요하다.
그리고 Child useState 같은경우 검색창을 생성시킬때마다 작동한다.

이 원리를 잘 이해하지 못하면 만들고 버그가 걸릴수도 있다.
```
