# Build Yapısını Tanıma
`npx create-react-app` ile bir uygulama oluşturduğumuzda elimizde bir yapı olacaktır. Burada public klasörü ön yüzümüzü gösterirken src içinde asıl olaylar dönecektir. src yapısı içinde App.js dosyası bizim dönen kısımları döndüren yer burasıdır. Yani tüm componentler bu App içinde birleşecektir.  index.js ise bizim render işlemini alır.

# İlk Uygulamamızı Yazma

Öncelikle ilk uygulamamız için App.js içinde düzenlemeye gidelim.

```jsx
import logo from './logo.svg';  
import './App.css';  
import Header from "./components/Header";  
  
function App() {  
  return (  
    <div>  
      <h1>Selam Dünya</h1>  
      <Header/>    
	</div>  
  )  
}  
  
export default App;
```

Şimdi de kendimize bir Header açalım. Gereken dizin yukarıda görünüyor.

```jsx:components/Header.js
function Header(){  
  return(  
    <div>  
      Merhaba Ben Header Bileşeniyim  
    </div>  
  )  
}  
  
export default Header;
```

Bu sayede Header artık App.js içinde görünecektir.

>[!danger] Dikkat
>React içinde büyük harfle başlayanlar birer component ve küçük başlayanlar normal etiket olarak görülecektir.

>[!danger] Dikkat
>React tek bir parent element return etmeyi beklemektedir. Birden fazla element return edilecekse de en azından fragment kullanılması gerekir. Yani 
>```jsx
>return (  
><>  
>   <Header/>    
>   <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nostrum, ratione.
> </p>
> </>
> )
> ```
