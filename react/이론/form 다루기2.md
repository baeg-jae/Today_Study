```
form 다루기

기본에 이어가기
validation
value
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
        const [message, setMessage] = React.useState("");
        const [phoneNumber, setPhoneNumber] = React.useState("");

        const handleSubmit = (event) => {
          event.preventDefault();
          alert(phoneNumber);
          // const phoneNumber = event.target.elements.phone.value;
          // if (phoneNumber.startsWith(0)) {
          //   alert("Good");
          // } else {
          //   alert("Bad");
          // }
        };

        const handleChange = (event) => {
          if (event.target.value.startsWith(0)) {
            setMessage("Phone Number is valid");
            setPhoneNumber(event.target.value);
          } else if (event.target.value.length === 0) {
            setPhoneNumber("");
            setMessage("");
          } else {
            setMessage("Phone Number should starts with 0");
          }
        };

        return (
          <form onSubmit={handleSubmit}>
            <label htmlFor="phone">Phone Number: </label>
            <br />
            <input
              id="phone"
              name="phone"
              onChange={handleChange}
              value={phoneNumber}
            />
            <p>{message}</p>
            <br />
            <br />
            <button
              type="submit"
              disabled={
                phoneNumber.length === 0 || message !== "Phone Number is valid"
              }
            >
              Submit
            </button>
            <p>{phoneNumber}</p>
          </form>
        );
      };
      ReactDOM.render(<App />, rootElement);
    </script>
  </body>
</html>
```
```

useState에 시차가 있어서 
const = phoneNumber = event.target.value 로 설정하여서
if(phoneNumber.startsWith(0)) 를 사용할때

useState에 걸려 있기 때문에 늦게 적용될수도 있다.
그러므로 if(event.target.value.startsWith(0))로 풀어서 사용하면 event.target.value 값을 바로 들고와서
시차?를 극복할수있다.
```
