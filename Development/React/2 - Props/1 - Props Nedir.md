# Props Nedir

Örneğin bir komponente parametre gönderim bu parametrenin durumuna göre komponenti çalıştırmak isteyebiliriz. Buradaki props kısmından kastımız tıpkı HTML içindeki attribute ile aynı mantıktadır. Bunları komponente `props` değişkeni olarak veya belirlediğimiz bir değişkende gönderip çağırabiliriz.

```jsx:components/User.js
function User(props){  
    return <div>{props.name} {props.surname}</div>  
}  
  
export default User;
```

```jsx:App.js
import './App.css';  
import User from "./components/User";  
  
const name = "Furkan"  
const surname = "Taşkın"  
const isLoggedIn = true;  
  
function App() {  
    return (  
        <>  
            <User name="Furkan" surname="Taşkın"/>  
        </>    )  
}  
  
export default App;
```

[[4 - Koşullu Render İşlemi]] içinde gördüğümüz koşullu render olayını burada props ile de yapabiliriz. Örnek olarak

```jsx:App.js
import './App.css';  
import User from "./components/User";  
  
  
function App() {  
    return (  
        <>  
            <User name="Furkan" surname="Taşkın" isLoggedIn={true}/>  
        </>    )  
}  
  
export default App;
```

```jsx:User.js
function User(props){  
    return (  
        <h1>  
            {  
                props.isLoggedIn ? `${props.name} ${props.surname}` : "Giriş Yapmadınız"  
            }  
        </h1>  
    )  
}  
  
export default User;
```

Burada sürekl olarak `props.name` gibi sürekli nesne tanımlamaları yerine nesne içindekileri birer argüman olarak da gönderip yazımda kolaylık sağlayabiliriz. Tek yapmamız gereken argümanları bir nesne olarak göndermek.

```jsx:User.js
function User({name, surname, isLoggedIn}){  
    return (  
        <h1>  
            {  
                isLoggedIn ? `${name} ${surname}` : "Giriş Yapmadınız"  
            }  
        </h1>  
    )  
}  
  
export default User;
```

