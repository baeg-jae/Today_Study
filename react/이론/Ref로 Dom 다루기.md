```
Ref로 Dom 다루기

Input Element가 있고 화면이 뜨자마자 focus를 주고 싶다면?

?.focus();

왜 이걸 Dom 조작하기라고 할까?
Element 조작하기가 아닌가?
```
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
      const App = () => {
        const inputRef = React.useRef();
        const divRef = React.useRef();
        React.useEffect(() => {
          inputRef.current.focus();
          // document.getElementById("input").focus();

          setTimeout(() => {
            divRef.current.style.backgroundColor = "pink";
          }, 1000);
        }, []);
        return (
          <>
            <input ref={inputRef} />
            <div
              ref={divRef}
              style={{ height: 100, width: 300, backgroundColor: "brown" }}
            />
          </>
        );
      };
      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>
```
```
why React?

document.getElementById류를 사용하지 않고
useRef라는 별도의 방법을 제공할까?
리액트가 틀안에서 스스로 하기위해서 이 방법을 제공한다.


Ref로 Dom 다루기

Vanilla JS -> document.get~ / document.query~
React -> useRef/ ref
```
