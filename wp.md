**соглашение** 
```
[acceptance acceptance-783 class:contact-acceptance2-modal ]
```
**Даю согласие на обработку**
```
<a target="_blank" href="/politika-konfidencialnosti/" rell="nofollow" id="consent">персональных данных*</a> [/acceptance]
```
**маска телефона cf7**
```
[mask* mask-tel class:cf7_tel maxlength:40 placeholder"Введите телефон*" "+7 (___) ___-__-__" ]
```
**wp**
```
 $category = get_queried_object();
    $current_cat_id = $category->term_id;
    $current_cat_name = $category->name;
   ```
**wp подключение стилей**
```
<?php  echo get_template_directory_uri()  ?>/
```
**домашняя директория**
```
<?php echo get_home_url()  ?>/
```
**шорткод**
```
<?php echo do_shortcode('');  ?>
```
**ACF**
```
<?php the_field('имя_поля'); ?>
```
**ACF ГРУППА**
```
<?php
$hero = get_field('group');
if( $hero ): ?>
    <div class="col">  
  <?phpecho $hero['text'];  ?>  
<a data-fancybox="doctor" href="<?php echo esc_url( $hero['doctor_spec6']['url'] ); ?> "> <img alt="<?php  the_title('', ''); ?>" src="<?php echo esc_url( $hero['doctor_spec6']['url'] ); ?> "  /> </a> </div>    
<?php endif; ?>
```

**или**
```
<?php $hero = get_field('group_img');  ?>
<?php if (!empty($hero['doctor_spec_img']['url'])) {  ?>    <div class="doctor_slide_img">  <a data-fancybox="doctor" href="<?php echo esc_url( $hero['doctor_spec_img']['url'] ); ?> "> <img alt="<?php  the_title('', ''); ?>" src="<?php echo esc_url( $hero['doctor_spec_img']['url'] ); ?> "  /> </a>  </div><?php } ?>
```
**ACF пустота**
```
<?php if( get_field("field_name") ): ?> контент<?php endif; ?>
```
**ACF пустота**
```
<?php
               $bread_term = get_queried_object();
               $bread = get_field('breadcrumbs', $bread_term);
               if (!empty($bread)) {
                   echo  ' <span>  ' .$bread.' </span> ';
               }  else {   ?>  
               <span></span>
           <?php } ?>
     ```
**ACF вывести в категориях**
```
$doctor_category_h1 = get_queried_object();
elseif (  get_field( 'doctor_category_h1', $doctor_category_h1 ) )   {  ?>   <h1 class="page-title">  <?php   the_field( 'doctor_category_h1', $doctor_category_h1 );  ?></h1> <? }
```
**Страницы**
```
<?php if (is_page('Главная'))
{
echo"ggggggggggg";
}
else
{
} ?>
```
**если содержит url**  
<?php   $parsed = parse_url(get_site_url( null, null, null ));
$host_custom = $parsed['host'];
$host_custom_url = $_SERVER['SERVER_NAME'] . $_SERVER['REQUEST_URI'];
if($host_custom_url ==  "$host_custom/doctor/bishal-battaray/")  {  } ?>
если содержит url       <?php   /*условие для title */
               $parsed = parse_url(get_site_url( null, null, null ));
$host4 = $parsed['host'];
              $host = $_SERVER['SERVER_NAME'] . $_SERVER['REQUEST_URI'];
              if($host ==  "$host4/doctor/")  {  echo  '  <title >Все доктора</title>';  }
elseif    ($host ==  "$host4/blog/")   {    echo  '  <title >Блог</title>';   }
else  {  ?>      <title class="page-title"> <?php echo esc_html($page_title) ?> </h1>    <?php  } ?>
если главная страница     <?php   if( is_front_page() ) { //код }    ?>
вп вывод записей
<?php
global $post;
$args = array( 'post_type'=>'post', 'post_status'=>'publish', 'posts_per_page'=>-1);
$myposts = get_posts( $args );
foreach( $myposts as $post ){ setup_postdata($post);   ?>
<div class="col-sm newsitem"  >
             <div class="news2">
              <a href="<?php the_permalink(); ?>"> <?php the_post_thumbnail('thumbnail'); ?></a>
             <div class="news3">
           <a href="<?php the_permalink(); ?>">     <h3><?php the_title(); ?></h3>   </a>
             <p><?php echo get_the_date(); ?></p>
           </div>
           </div>
          </div>    
<?php    }    wp_reset_postdata();   ?>  
// Заменяем тег <H2> на <p> у товаров
remove_action( 'woocommerce_shop_loop_item_title', 'woocommerce_template_loop_product_title', 10 );
add_action( 'woocommerce_shop_loop_item_title', 'custom_woocommerce_template_loop_product_title', 10 );
function custom_woocommerce_template_loop_product_title() {
   echo '<p class="' . esc_attr( apply_filters( 'woocommerce_product_loop_title_classes', 'woocommerce-loop-product__title' ) ) . '">' . get_the_title() . '</p>';
}
// конец Заменяем тег <H2> на <p> у товаров
// Отключить генерация картинок
вывод массива add_action('after_setup_theme', function() {
echo '<pre>';
print_r(wp_get_additional_image_sizes());
echo '</pre>';
die();
}, 999);
функция  
// Отключить генерация картинок
function dco_remove_default_image_sizes( $sizes) {
   return array_diff( $sizes, array(
       'fastroad-thumb-78-78',
 'fastroad-thumb-78-78'
) );}
add_filter('intermediate_image_sizes', 'dco_remove_default_image_sizes');
//конец Отключить генерация картинок
//начало скрыть от индексации пагинацию первый способ
function wpschool_noindex_paged() {    if ( is_paged() ){   ?>
           <meta name="robots" content="noindex,nofollow">    <?php  }  }
add_action( 'wp_head', 'wpschool_noindex_paged', 2 );
//скрыть от индексации пагинацию второй способ
add_filter( 'wp_robots', 'wp_robots_remove_noindex', 999 );
function wp_robots_remove_noindex( $robots ){
 if ( is_search() ||  is_paged() || is_archive(  ) || is_404(  ) ) {
   $robots[ 'noindex' ] = true;
   $robots[ 'nofollow' ] = true;    }
 return $robots;    }
//конец скрыть от индексации пагинацию
//запрет обновления плагинов
add_filter( 'site_transient_update_plugins', 'filter_plugin_updates' );
function filter_plugin_updates( $value ) {
   unset( $value->response['updraftplus/updraftplus.php'] );
   unset( $value->response['advanced-custom-fields-pro/acf.php'] );
   unset( $value->response['elementor/elementor.php'] );
   return $value;
} //конец запрет обновления плагинов
//скрыть от индексации только страницы пагинацию третий способ
add_filter( 'wp_robots', 'wp_robots_remove_noindex', 999 );
function wp_robots_remove_noindex( $robots ){
  if ( is_paged()  ) {
    $robots[ 'noindex' ] = true;
    $robots[ 'follow' ] = true;
      }
  return $robots;    }
//конец скрыть от индексации только страницы пагинацию третий способ
//изменить комментарии, их форму
add_filter('comment_form_defaults', 'ocean_custom_comment_title', 20);
function ocean_custom_comment_title( $defaults ){
 $defaults['title_reply'] = __('Оставить комментарий', 'customizr-child');
 $defaults['label_submit'] = __('Отправить', 'customizr-child');
 $defaults['fields']['author'] = __('<p class="comment-form-author"><input id="author" class="comment-form__field" name="author" type="text" placeholder="Ваше имя*" value="" size="30" aria-required="true" required="required"></p>', 'customizr-child');
 $defaults['fields']['email'] = __('<p class="comment-form-email"><input id="email" class="comment-form__field" name="email" type="text" placeholder="Ваш e-mail *" value="" size="30" aria-describedby="email-notes" aria-required="true" required="required"></p>', 'customizr-child');
 $defaults['comment_field'] = __('<p class="comment-form-comment"><textarea id="comment" class="comment-form__field" name="comment" placeholder="Ваш комментарий *" cols="45" rows="8"  aria-required="true" required="required"></textarea></p>', 'customizr-child');
 return $defaults;
}
//конец изменить комментарии, их форму
//свой шорткод
//добавить в функцию
include( get_template_directory() . "/assets/shortcodes/posts.php" );  
сам шорткод, вызов [postscustom]
<?php
function get_postscustom($atts) {
   ob_start();
   ?>
ok
   <?php  return ob_get_clean();  }
add_shortcode('postscustom', 'get_postscustom');
//конец свой шорткод
//гугл аналитика
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-113043865-1"></script>
<script>window.dataLayer = window.dataLayer || [];
function gtag(){dataLayer.push(arguments);}
gtag('js', new Date());
gtag('config', 'UA-113043865-1');</script>
<script type="text/javascript">
 document.addEventListener('wpcf7mailsent', function sendMail(event) {
   if ('5356' == event.detail.contactFormId) {
       gtag('event', 'send', {
       'event_category': 'Consultation',
       'event_action': 'Submit'
     });
     yaCounter47318817.reachGoal('zakaz');
   
   }
 }, false);
</script>
//конец гугл аналитика
//консоль вп заметки
function console_note() { ?>
  <a href="/wp-admin/edit.php?post_type=acf-field-group">  Группа полей</a>
   <?php }
function add_console_note() {     wp_add_dashboard_widget( 'console_note', __( 'Заметки' ), 'console_note' );  }
add_action('wp_dashboard_setup', 'add_console_note' );
//конец консоль вп заметки
