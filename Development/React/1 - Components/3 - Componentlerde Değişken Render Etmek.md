# Değişken Renderlama

Örnek olarak elimizde bir isim olsun ve bunu ekrana gösterelim. Bunu çok rahat yapabiliriz. Bunun için süslü parantez kullanmamız yeterlidir. 

```js:App.js
import './App.css';  
  
const name = "Furkan"  
  
function App() {  
    return (  
        <>  
            <h1>{name}</h1>  
        </>    
	)  
}  
  
export default App;
```
Çıktısı bize Furkan yazan bir h1 etiketi olacaktır. Burada dilersek string yapısı ile de çalışabiliriz.

```jsx:App.js
import './App.css';  
  
const name = "Furkan"  
  
function App() {  
    return (  
        <>  
            <h1>{name}</h1>  
            <p>{`Merhabalar ben ${name}`}</p>  
        </>    
	)  
}  
  
export default App;
```