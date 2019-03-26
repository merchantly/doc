## Страница товара

А каждой странице товара существует переменная `gon.product` - объект, который присутствует в Javascript, на странице товара и содержит следующие поля:

* `name` - имя товара с артикулом
* `url` - ссылка на страницу товара (как правило совпадает с текущей)
* `price` - цена товара (число с плавающей запятой)
* `image_url` - ссылка на изображение товара (если оно есть)

Например для `carrotquest` использование этих данных будет таким:

```
if (gon.product) {
  carrotquest.track('$cart_added', {
    "$name": gon.product.name,
    "$url": gon.product.url,
    "$amount": gon.product.price,
    "$img": gon.product.image_url,
  });
};
```


## Кнопка "Добавить в корзину"

Кнопка имеет особый класс `.b-btn-add-cart`. Для события добавления в корзину используйте его.


## В помощь событиям на submit

```js
event_helper_submit('new_vendor_registration_form', function() { convead('event', 'submit_form'); }));
```


Где `new_vendor_registration_form` - id элемента формы


## События на странице

### В момент добавления товара в корзину `m.add-to-cart`

```
var handler = function(event, productData, amount) { console.log('add-to-cart', event, productData, amount); }
$(window).on('m.add-to-cart', handler);
```
