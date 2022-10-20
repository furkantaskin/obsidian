- [[#Prop Tipleri Tanımlama|Prop Tipleri Tanımlama]]
- [[#Prop için `isRequired` Kullanımı|Prop için `isRequired` Kullanımı]]
- [[#Birden Fazla Tipli Prop (`oneOfType`)|Birden Fazla Tipli Prop (`oneOfType`)]]
- [[#Shape Gönderme (`shape`)|Shape Gönderme (`shape`)]]
- [[#Prop için Varsayılan Değer Verme|Prop için Varsayılan Değer Verme]]


# Prop Tipleri Tanımlama 

Property içinde hangi veri tipini aldığımız belirtmek için component içinde property tipini belirtmemiz gerekmektedir. Bunu `PropTypes` ile rahat bir şekilde yapabiliriz. Örneğin User içinde tanımladığımız özelliklerin türlerini belirtebiliriz.

```jsx:components/User.js
import PropTypes from "prop-types"  
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
  
User.propTypes = {  
    name: PropTypes.string,  
    surname: PropTypes.string,  
    isLoggedIn: PropTypes.bool,  
    age: PropTypes.number,  
    friends: PropTypes.array  
}  
  
export default User;
```

# Prop için `isRequired` Kullanımı
Eğer elimizdeki proplar için doldurulması gereken alanlar varsa bu alanların hangilerinin doldurulması gerektiğini belirtebiliriz. Örneğin name için `isRequired` kullanalım

```jsx:components/User.js
import PropTypes from "prop-types"  
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
  
User.propTypes = {  
    name: PropTypes.string.isRequired,  
    surname: PropTypes.string,  
    isLoggedIn: PropTypes.bool,  
    age: PropTypes.number,  
    friends: PropTypes.array  
}  
  
export default User;
```

# Birden Fazla Tipli Prop (`oneOfType`)

Örneğin yaş için string ya da integer gönderebiliriz. Bunu `oneOfType` olarak gönderebiliriz. 

```jsx:components/User.js
import PropTypes from "prop-types"  
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
  
User.propTypes = {  
    name: PropTypes.string.isRequired,  
    surname: PropTypes.string,  
    isLoggedIn: PropTypes.bool,  
    age: PropTypes.oneOfType([PropTypes.number, PropTypes.string]).isRequired,  
    friends: PropTypes.array  
}  
  
export default User;
```

>[!tip] İPUCU
>Dilersek `isRequired` ile de bu kısmı zorunlu alan yapabiliriz.

# Shape Gönderme (`shape`)
Prop bu kısımda tek bir yapı olmayabilir. Bir nesne veya altında birden fazla veri içeren bir yapı da olabilir. Bu durumda alt proplerın türünü belirtmek için `shape` metodunu kullanırız.

```jsx:components/User.js
import PropTypes from "prop-types"  
  
function User({name, surname, isLoggedIn, friends, address}) {  
  return (  
    <>  
      <h1>        {  
          isLoggedIn ? `${name} ${surname}` : "Giriş Yapmadınız"  
        }  
  
      </h1>  
        {address.title} {address.zip}  
      {  
        friends.map((friend, index) => <p key={index}> {friend}</p>)  
      }  
    </>  
  )  
}  
  
User.propTypes = {  
  name: PropTypes.string.isRequired,  
  surname: PropTypes.string,  
  isLoggedIn: PropTypes.bool,  
  age: PropTypes.oneOfType([PropTypes.number, PropTypes.string]),  
  friends: PropTypes.array,  
  address: PropTypes.shape({  
      title: PropTypes.string,  
      zip: PropTypes.number  
  })  
}  
  
export default User;
```

```jsx:App.js
import './App.css';  
import User from "./components/User";  
  
  
function App() {  
    return (  
        <>  
            <User name="Furkan" surname="Taşkın" isLoggedIn={true} friends={["Ahmet", "Mehmet", "Ayşe", "Fatma"]} address={{  
                title: "Selçuklu / Konya",  
                zip: 42060  
            }}/>  
        </>    
        )  
}  
  
export default App;
```

# Prop için Varsayılan Değer Verme

`.defaultProps` yapısı ile değer verilmemiş proplara varsayılan bir değer atabiliriz. Bunu fonksiyonlarda argümanlara verilen bir placeholder değişken olarak düşünebiliriz. Mesela kullanıcı için `isLoggedIn` durumu varsayılan olarak false olsun. Eğer biz bunu prop içinde göndermezsek bu sürekli olarak false kalacaktır.

```jsx:components/User.js
import PropTypes from "prop-types"  
  
function User({name, surname, isLoggedIn, friends, address}) {  
  return (  
    <>  
      <h1>        {  
          isLoggedIn ? `${name} ${surname}` : "Giriş Yapmadınız"  
        }  
  
      </h1>  
        {address.title} {address.zip}  
      {  
        friends.map((friend, index) => <p key={index}> {friend}</p>)  
      }  
    </>  
  )  
}  
  
User.propTypes = {  
  name: PropTypes.string.isRequired,  
  surname: PropTypes.string,  
  isLoggedIn: PropTypes.bool,  
  age: PropTypes.oneOfType([PropTypes.number, PropTypes.string]),  
  friends: PropTypes.array,  
  address: PropTypes.shape({  
      title: PropTypes.string,  
      zip: PropTypes.number  
  })  
}  
  
User.defaultProps = ({  
    isLoggedIn: false  
})  
  
export default User;
```

```jsx:App.js
import './App.css';  
import User from "./components/User";  
  
  
function App() {  
    return (  
        <>  
            <User name="Furkan"  
                  surname="Taşkın"  
                  // isLoggedIn={true}  
                  friends={["Ahmet", "Mehmet", "Ayşe", "Fatma"]}  
                  address={{  
                    title: "Selçuklu / Konya",  
                    zip: 42060  
                  }}  
            />  
        </>    )  
}  
  
export default App;
```


# Ekstra: If / Else Kullanımı

Diyelim ki burada çok sayıda return edilecek durum olsun. Bunların hepsini ternary operatör ile yaparsak okunabilirlik azalacaktır. Bunu büyük if/else bloğu ile yapabiliriz. Burada erken bir return döndürme işlemi yaparız. Fonksiyonlarda sistem ilk gördüğü return ifadesinden sonraki kodları çalıştırmayacağı için `isLoggedIn` ifadesinin false olması durumunda direkt olarak uyarı verecektir.

```jsx:components/User.js
import PropTypes from "prop-types"  
  
function User({name, surname, isLoggedIn, friends, address}) {  
  if(!isLoggedIn){  
    return <div>Giriş Yapmadınız</div>  
  }  
  return (  
    <>  
      <h1>        {  
          isLoggedIn ? `${name} ${surname}` : "Giriş Yapmadınız"  
        }  
  
      </h1>  
      {address.title} {address.zip}  
      {  
        friends.map((friend, index) => <p key={index}> {friend}</p>)  
      }  
    </>  
  )  
}  
  
User.propTypes = {  
  name: PropTypes.string.isRequired,  
  surname: PropTypes.string,  
  isLoggedIn: PropTypes.bool,  
  age: PropTypes.oneOfType([PropTypes.number, PropTypes.string]),  
  friends: PropTypes.array,  
  address: PropTypes.shape({  
      title: PropTypes.string,  
      zip: PropTypes.number  
  })  
}  
  
User.defaultProps = ({  
    isLoggedIn: false  
})  
  
export default User;
```