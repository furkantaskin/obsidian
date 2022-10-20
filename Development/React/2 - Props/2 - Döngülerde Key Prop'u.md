Şimdi elimizdeki component içine prop olarak array verip bunu komponent altında listelemek isteyebiliriz. Bunu yapmak için de dizi yapısı ile prop tanımlayabiliriz. Burada her bir elemanı `.map()` ile döndürebiliriz. Bu konuyu [[Development/JS/Giriş]] içinde görmüştük.

![[Giriş#^b65988]]
![[Development/JS/Giriş#^2891a3]]

Bunları da React içinde rahatça kullanabiliriz.

```jsx:components/User.js
function User({name, surname, isLoggedIn, friends}){  
    return (  
        <h1>  
            {  
                isLoggedIn ? `${name} ${surname}` : "Giriş Yapmadınız"  
            }  
            {  
                friends.map((friend) => <p>{friend}</p>)  
            }  
        </h1>  
    )  
}  
  
export default User;
```

```jsx:App.js
import './App.css';  
import User from "./components/User";  
  
  
function App() {  
    return (  
        <>  
            <User name="Furkan" surname="Taşkın" isLoggedIn={true} friends={["Ahmet", "Mehmet", "Ayşe", "Fatma"]}/>  
        </>    )  
}  
  
export default App;
```

Ancak burada konsolu açtığımızda her bir alt elementin bir eşsiz key değerine sahip olması gerektiğini söyleyecektir. Bunun anlamı:

Map yaptığımız liste içindeki elemanların performans kaybı yaşamadan listelenmesi için bizden React bir key propu beklemektedir. Bununla ilgili durum, [React dokümnatasyonunda](https://beta.reactjs.org/learn/rendering-lists#why-does-react-need-keys) net bir şekilde açıklanmıştır. Bunu `.map()` içinde gelen `index` değeri ile yapabiliriz.

```jsx:User.js
function User({name, surname, isLoggedIn, friends}){  
    return (  
        <h1>  
            {  
                isLoggedIn ? `${name} ${surname}` : "Giriş Yapmadınız"  
            }  
            {  
                friends.map((friend, index) => <p key={index}> {friend}</p>)  
            }  
        </h1>  
    )  
}  
  
export default User;
```

Artık değer key attribute içinde dönecektir. Ancak bunlar ön kısımda gösterilmeyecektir. Çıktısı

```html
<h1>Furkan Taşkın
	<p> Ahmet</p>
	<p> Mehmet</p>
	<p> Ayşe</p>
	<p> Fatma</p>
</h1>
```

Burada `return` olayının içinde bu işlemleri yapmak zorunda değiliz. Dilersek her bir elementi ayrı ayrı return edebiliriz.