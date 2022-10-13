- [[#Strict Kullanımı|Strict Kullanımı]]
- [[#Değişkenler|Değişkenler]]

# Kod Yapısı

JS içerisinde noktalı virgül kullanımı zorunlu değildir. Python gibi yeni satırlar da yeni kod olarak görülebilir. Ancak bazı durumlarda noktalı virgül kullanımı önem arz etmektedir.

# Strict Kullanımı

`"use strict"` ECAScript 5 ile gelen bir moddur.

Uzun bir süre uyumluluk sorunu olmadan gelişen JS, yeni özellikleri benimserken eski özellikleri de içinde tutmaya devam etti. Eski kodlarda bozulma olmasa da geliştirme aşamasında yapılabilecek herhangi bir hatadan dolayı bu kalıcı olarak sistemde barınabilir. ES5 ile gelen `"use strict"` sayesinde normalde gözardı edilen hatalar artık strict içerisinde direkt olarak hata verecektir. Bu sayede daha güvenli bir JS kodu yazılabilir.

# Değişkenler

JS içerisinde ES ile gelen yeni değişken türleri vardır. Normalde `var` ifadesi uzun yıllar boyunca aramızda yaşarken bu yapı ile yapılan tanımlamlar global olarak yaşamaktadır. Büyük yapılarda aynı değişken adından dolayı sistem hata ile karşılaşabilir. Bunun önüne geçebilmek için blok yapısında tanımlama yapabilmek amacıyla `const` ve `let` olmak üzere iki yapı daha eklendi.

`let` blok içinde lokal tanımlama yapmayı sağlarken `const` buna ek olarak sabit değişken tanımlaması yapmayı sağlamaktadır.