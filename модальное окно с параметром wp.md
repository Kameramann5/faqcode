**в письме cf7 указать**
```
[hidden tarif id:tarif ]
```
**Тариф:**
```
[tarif]
```
**вывод тарифа после названия в всплыв форме в cf7**
```
<p id="mdl_zakaz_title"></p>
```
**кнопка**
```
<a class="elementor-price-table__button elementor-button elementor-size-md" href="#" data-title="Стоимость услуг проектирования зданий и сооружений до 250 кв. м. Объекты малоэтажного строительства">Заказать</a>
или
<button id="" type="button" class="mdl-button show-modal-example">Заказать</button>
конец кнопка
```
```
<!-- всплывающая форма -->
<dialog class="mdl-dialog" id="modal-zakaz">    <div class="mdl-dialog__content">
       <?php echo do_shortcode( '[contact-form-7 id="13836" title="Всплывающая форма заказа"]' ); ?>
   </div>      <button type="button" class="mdl-dialog-close">Закрыть</button>     </dialog>
   <script src="<?php echo get_template_directory_uri() ?>/assets/js/my2.js"></script>
   <!-- конец всплывающая форма -->
   ```
   ```
/*стилизация ошибок*/
.mdl-dialog span[role="alert"] {
 position: absolute;
 top: 14px;
 padding-left: 17px;
 width: 313px;
 font-size: 13px;
}
.mdl-dialog  .wpcf7-not-valid-tip  {
 position: absolute;
 top: 14px;
 padding-left: 17px;
 width: 313px;
 font-size: 13px;
}
/*конец стилизация ошибок*/
```
```
/*кнопка закрытия в виде креста*/
 .mdl-dialog-close {       position: absolute;
   top: 3px;    border: none;
   background: white;
   right: 12px;
   width: 18px;
   height: 22px;
   cursor: pointer;}
   .mdl-dialog-close:after {
     content: '';
     background-color: #e41f25;
     position: absolute;
     height: 3px;
     width: 24px; transition: 0.3s;
     top: 11px;
     transform: rotate(45deg);
     left: -4px;
   }
.mdl-dialog-close:before {
 content: '';
 background-color: #e41f25;
 position: absolute; transition: 0.3s;
 height: 3px;
 width: 24px;
 top: 11px;
 left: -4px;
 transform: rotate(-45deg);
   }
   .mdl-dialog-close:hover:after {    background-color: #595959;  transition: 0.3s;     }
   .mdl-dialog-close:hover:before {    background-color: #595959;  transition: 0.5s;     }
/*конец кнопка закрытия в виде креста*/
```
**затемнение фона**
```
dialog::backdrop {  background: rgba(138, 138, 138, 0.65);}
```
```
 /* всплывающая форма*/
 dialog::backdrop {  background: rgba(138, 138, 138, 0.65);}
 .mdl_zakaz {     color: #e41f25;
   font-family: Roboto, sans-serif;
   font-weight: 600;
   font-size: 23px;
   line-height: 27px; }
.mdl-button  {    /* background: #154600;
 text-decoration: underline;
 padding: 16px 25px;*/}
 .mdl-button:hover {  /*  background: #DA4453;*/ }
 .mdl-dialog  label {      color: rgba(0,0,0,.54);}
 .mdl-dialog  .wpcf7-acceptance input[type="checkbox"]:before {      border: 1px solid #e41f25; }
 .mdl-dialog .wpcf7-list-item-label a   {    color: #e41f25;  }
 .mdl-dialog .wpcf7-list-item-label a:hover   {    color: #c1c1c1;  }
.mdl-dialog {
 text-align: left;
 border: none;
 box-shadow: 0 9px 46px 8px rgba(0, 0, 0, 0.14), 0 11px 15px -7px rgba(0, 0, 0, 0.12), 0 24px 38px 3px rgba(0, 0, 0, 0.2);
 width: 400px; }
 .mdl-dialog  input {    font-weight: 400;}
 .mdl-dialog__title {
   padding: 24px 24px 0;
   margin: 0;
   font-size: 2.5rem; }
 .mdl-dialog__actions {
   padding: 8px 8px 8px 24px;
   display: -webkit-flex;
   display: -ms-flexbox;
   display: flex;
   -webkit-flex-direction: row-reverse;
       -ms-flex-direction: row-reverse;
           flex-direction: row-reverse;
   -webkit-flex-wrap: wrap;
       -ms-flex-wrap: wrap;
           flex-wrap: wrap; }
   .mdl-dialog__actions > * {
     margin-right: 8px;
     height: 36px; }
     .mdl-dialog__actions > *:first-child {
       margin-right: 0; }
   .mdl-dialog__actions--full-width {
     padding: 0 0 8px 0; }
     .mdl-dialog__actions--full-width > * {
       height: 48px;
       -webkit-flex: 0 0 100%;
           -ms-flex: 0 0 100%;
               flex: 0 0 100%;
       padding-right: 16px;
       margin-right: 0;
       text-align: right; }
 .mdl-dialog__content {
   padding: 20px 24px 24px 24px;
   color: rgba(0,0,0, 0.54); }
 .mdl-dialog-close {    background-color: #e41f25;
   color: white;
   border: none;
   text-transform: uppercase;
   font-size: 11px;
   padding: 7px;
   font-family: Roboto, sans-serif; }
     /* конец всплывающая форма*/
  ```
     
**скрипт**

  **/*модальное окно на страницах
  для передачи параметра тариф, заполнить у ссылки кнопки в элементоре произвольные атрибуты
  пример: data-title|Стоимость услуг проектирования зданий и сооружений свыше 700 кв. м. Объекты малоэтажного строительства
  */**
  ```
  (function() {
   'use strict';
   var dialog = document.querySelector('#modal-zakaz');
   var closeButton = dialog.querySelector('.mdl-dialog-close');
   var showButton = document.querySelectorAll(".elementor-price-table__button");
   for (let elem of showButton) {
   //var showButton = document.querySelector('.show-modal-example');
   if (! dialog.showModal) {
     dialogPolyfill.registerDialog(dialog);
   }
   var closeClickHandler = function(event) {
     dialog.close();
   };
   var showClickHandler = function(event) {
     dialog.showModal();
   };
   elem.addEventListener('click', showClickHandler);
   //showButton.addEventListener('click', showClickHandler);
   closeButton.addEventListener('click', closeClickHandler);
 }  }());
 ```
 
**//для передачи параметра data-title у ссылки в вывод  в модальное окно и установление его как скрытое поле для передачи на почту cf7**
```
 jQuery('.elementor-price-table__button').click(function(evet) {
   event.preventDefault();
   const formTitle = jQuery(this).attr('data-title');
   jQuery('#tarif').val(formTitle);
   jQuery('#mdl_zakaz_title').html(formTitle);
 });
 jQuery('.mdl-dialog-close').click(function(evet) {
   event.preventDefault();
   const formTitle = jQuery(this).attr('data-title');
   jQuery('#tarif').val('');
   jQuery('#mdl_zakaz_title').html('');
 });
 ```
**упрошенный вариант**
```
var result = document.getElementsByClassName("fio_page_hidden")[0].innerHTML;
console.log(result);
jQuery('#fio_hidden').val(result);
```
