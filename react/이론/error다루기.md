```
error 다루기

catch error

try{
...
} catch(error) {
...
}
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

      class ErrorBoundary extends React.Component {
        //에러가 뜨면 특정한 페이지를 보여주겠다. 모든 페이지를 핸들링하겠다.
        state = { error: null };
        static getDerivedStateFromError(error) {
          return { error };
        }
        render() {
          const { error } = this.state;
          if (error) {
            return <this.props.fallback error={error} />;
          }
          return this.props.children;
        }
      }

      const Child = () => {
        throw new Error("Something Wrong ....");
        return <p>Child...</p>;
      };
      const Fallback = () => {
        return <p>There is some error...</p>;
      };
      const App = () => {
        return (
          <>
            <p>App</p>
            <ErrorBoundary fallback={Fallback}>
              <Child />
            </ErrorBoundary>
          </>
        );
      };
      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>
```
```


error 다루기
error boundary -> catch error 해서 보여주기
fallback -> error가 났을 때 보여줄 컴포넌트

```
