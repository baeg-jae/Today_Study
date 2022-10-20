```

key와 리렌더링 알아보기2

재사용 -> key를 제대로 줘야 재사용 가능
제대로 준다 -> 중복없고, 바뀌지 않는
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

      const todos = [
        [
          { id: 1, value: "Wash dishes" },
          { id: 2, value: "Clean the bed" },
          { id: 3, value: "Running" },
          { id: 4, value: "Learning" }
        ],

        [
          { id: 4, value: "Learning" },
          { id: 1, value: "Wash dishes" },
          { id: 2, value: "Clean the bed" },
          { id: 3, value: "Running" }
        ],
        [
          { id: 3, value: "Running" },
          { id: 4, value: "Learning" },
          { id: 1, value: "Wash dishes" },
          { id: 2, value: "Clean the bed" }
        ],
        [
          { id: 2, value: "Clean the bed" },
          { id: 3, value: "Running" },
          { id: 4, value: "Learning" },
          { id: 1, value: "Wash dishes" }
        ]
      ];

      const App = () => {
        const [items, setItems] = React.useState(todos[0]);

        React.useEffect(() => {
          const interval = setInterval(() => {
            const random = Math.floor(Math.random() * 3);
            setItems(todos[random]);
          }, 1000);
          return () => {
            clearInterval(interval);
          };
        }, []);

        const handleDoneClick = (todo) => {
          setItems((items) => items.filter((item) => item !== todo));
        };
        const handleRestoreClick = () => {
          setItems((item) => [
            ...items,
            todos.find((item) => !items.includes(item))
          ]);
        };
        return (
          <>
            {items.map((todo, index) => (
              <div key={index}>
                <button onClick={() => handleDoneClick(todo)}>
                  {todo.value}
                </button>
              </div>
            ))}
            <br />
            <button onClick={handleRestoreClick}>Restore</button>
          </>
        );
      };
      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>
```
