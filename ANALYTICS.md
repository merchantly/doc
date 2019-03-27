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

### В момент нажания на "Оформить заказ", из корзины: `m.cart-submit`

* `$(window).trigger('m.cart-submit', cartItems, packageItem);`

cartItems:

![cartItems](https://user-images.githubusercontent.com/31139/55071328-65398e80-5099-11e9-8f97-329ee246384b.png)

packageItem:

![packageItem](https://user-images.githubusercontent.com/31139/55071327-64a0f800-5099-11e9-876a-0cc20c199f69.png)

### В момент отображения страницы оформления заказа (ввод адреса и оплаты) `m.initial-checkout`

* `$(window).trigger('m.initial-checkout', cart, coupon);`

cart:

![cart](https://user-images.githubusercontent.com/31139/55071463-bc3f6380-5099-11e9-88ac-a0779af2abc8.png)

## product data example:

### home page or products list (category page)

![category page](https://user-images.githubusercontent.com/31139/55017048-fd376980-5000-11e9-9ac5-1b01501a6dcc.png)


### product page

![product page](https://user-images.githubusercontent.com/31139/55017160-34a61600-5001-11e9-9de8-b9e42feb0717.png)


### wishlist page

![Screen Shot 2019-03-26 at 19 54 12](https://user-images.githubusercontent.com/31139/55017048-fd376980-5000-11e9-9ac5-1b01501a6dcc.png)

## Данные в `gon`

* gon.controller_name - string
* gon.action_name -
* gon.product - object (exists only on product page)

### controller#action

* welcome#index - home page
* categories#show
* products#show
