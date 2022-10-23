```
https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch에

찾아서 해보았더니

.catch 오류가 계속뜸
``


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
        const [data, setData] = React.useState(null);

        React.useEffect(() => {
          fetch(
            "https://raw.githubusercontent.com/techoi/raw-data-api/main/simple-api.json"
          )
            .then(function (response) {
              return response.json()
            })
            .then(function (data) {
              setData(data.data)
            });
            .catch((error) => {
              console.log(error)
            })
        }, []);
        if (data == null) {
          return <p>Loading...</p>;
        }
        return (
          <div>
            <p>People</p>
            {data.people.map((person) => (
              <div>
                <span>name: {person.name} </span>
                <span>age: {person.age}</span>
              </div>
            ))}
          </div>
        );
      };
      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>
```
