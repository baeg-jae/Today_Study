처음 리액트를 들어가기전 js와 함께 공부하기로 하였습니다.

정리를 바로바로 해야하는데 산더미 처럼 쌓여서 최대한 간략하게 정리하게 되었습니다.


---------------------------------------------
이벤트 핸들러

바닐라 js
on{event} onclick, onmouseout, onfocus, onblur... /addEventListener



react js (카멜 케이스)
on{Event} onClick, onMouseOut, onFocus, onBlur ...



바닐라 js

<!DOCTYPE html>
<html>
<body>

<button id="button" onclick="document.getElementById('demo').innerHTML=Date()">The time is?</button>

<p id="demo"></p>
<script>
	const button = document.getElementById("button");
    button.addEventListener("mouseout", () => alert("bye"));
    button.addEventListener("click", () => alert("press"));
</script>

</body>
</html>



react js

<!DOCTYPE html>
<html lang="en">
  <body>
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <div id="root"></div>
    <script type="text/babel">
      const rootElement = document.getElementById("root");

      const handleClick = () => alert("pressed");
      const handleMouseOut = () => alert("bye");
      const element = (
        <button onClick={handleClick} onMouseOut={handleMouseOut}>
          Press
        </button>
      );
      ReactDOM.render(element, rootElement);
    </script>
  </body>
</html>


react js

<!DOCTYPE html>
<html lang="en">
  <body>
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <div id="root"></div>
    <script type="text/babel">
      const rootElement = document.getElementById("root");

      const handleClick = () => alert("pressed");
      const handleMouseOut = () => alert("bye");
      const element = (
        <button onClick={handleClick} onMouseOut={handleMouseOut}>
          Press
        </button>
      );
      ReactDOM.render(element, rootElement);
    </script>
  </body>
</html>

