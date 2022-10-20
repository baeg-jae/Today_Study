```
리액트 Element에 스타일 입히기

className -> 문자열
style -> 객체, 카멜케이스, className보다 먼저

```
```js

<!DOCTYPE html>
<html lang="en">
  <body>
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <div id="root"></div>
    <style>
      .button {
        background-color: #4caf50; /* Green */
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
      }

      .blue {
        background-color: #008cba;
      } /* Blue */
      .red {
        background-color: #f44336;
      } /* Red */
      .gray {
        background-color: #e7e7e7;
        color: black;
      } /* Gray */
      .black {
        background-color: #555555;
      } /* Black */
    </style>
    <script type="text/babel">
      function Button({ className = "", color, style, ...rest }) {
        return (
          <button
            className={`button ${className}`}
            style={{ backgroundColor: color, borderRadius: 8, ...style }}
            {...rest}
            //className = 클래스, 클래스보단 스타일이 우선이다.
            // style= 스타일,  color = 상자 색, rest = 글자 내용
          />
        );
      }

      const element = (
        <>
          <Button style={{ borderRadius: "50%" }}>Green</Button>
          <Button color="blue">Blue</Button>
          <Button color="red">Red</Button>
          <Button color="gray">Gray</Button>
          <Button color="black">Black</Button>
        </>
      );
      ReactDOM.render(element, document.getElementById("root"));
    </script>
  </body>
</html>

```
