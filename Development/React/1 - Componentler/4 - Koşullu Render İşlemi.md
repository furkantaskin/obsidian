Örneğin auth durumuna göre render işlemini değiştirmemiz lazım. Normalde [[3 - Componentlerde Değişken Render Etmek]] kısmında değişken tanımlamayı öğrenmiştik ancak her zaman düz bir yapı olmayabilir. Yeri geldiğinde çeşitli koşulları incelememiz gerekebilir. Bu durumda render işlemini koşul ile de kontrol edebiliriz.

```jsx:App.js
import './App.css';  
  
const name = "Furkan"  
const surname = "Taşkın"  
const isLoggedIn = false;  
  
function App() {  
    return (  
        <>  
            <p>{isLoggedIn && `Benim adım ${name} ve soyadım ${surname}`}</p>  
            {!isLoggedIn && "Giriş yapmanız gerekmektedir"}  
        </>  
    )  
}  
  
export default App;
```

Bunu ternary operatör ile de kısaltabiliriz

```jsx:App.js
import './App.css';  
  
const name = "Furkan"  
const surname = "Taşkın"  
const isLoggedIn = true;  
  
function App() {  
    return (  
        <>  
            {isLoggedIn  
                ? `Benim adım ${name} ve soyadım ${surname}`  
                : "Giriş yapmadınız"  
            }  
        </>  
    )  
}  
  
export default App;
```