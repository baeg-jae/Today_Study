```
Form 다루기

기본 Form

label
input
submit
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
        const handleSubmit = (event) => {
          event.preventDefault();

          console.dir(event.target);
          alert(
            `FirstName: ${event.target.fname.value}, LastName: ${event.target.lname.value}`
          );
        };
        return (
          <form onSubmit={handleSubmit}>
            <label htmlFor="fname">First name:</label>
            <br />
            <input type="text" id="fname" name="fname" defaultValue="John" />
            <br />
            <label htmlFor="lname">Last name:</label>
            <br />
            <input type="text" id="lname" name="lname" defaultValue="Doe" />
            <br />
            <br />
            <input type="submit" value="Submit" />
          </form>
        );
      };
      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>
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
        const handleSubmit = (event) => {
          event.preventDefault();

          console.dir(event.target);
          alert(
            `FirstName: ${event.target.elements.fname.value}, Choosed Car: ${event.target.elements.cars.value}`
          );
        };
        return (
          <form onSubmit={handleSubmit}>
            <label htmlFor="fname">First name:</label>
            <br />
            <input type="text" id="fname" name="fname" defaultValue="John" />
            <br />
            <label htmlFor="cars">Choose a car:</label>
            <select id="cars" name="cars">
              <option value="volvo">Volvo</option>
              <option value="saab">Saab</option>
              <option value="fiat">Fiat</option>
              <option value="audi">Audi</option>
            </select>
            <input type="submit" value="Submit" />
          </form>
        );
      };
      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>

```
