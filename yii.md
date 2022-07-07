**меню меняется в views/layouts/main.php**
<br/>
**чтобы создать новую страницу нужно в SiteController добавить**
```
  /*
     * Displays test page.
     */
    public function actionTest()
    {
      
        return $this->render('test');
    }
  ```
**и создать файл в views/site/test.php**
```
<?php
use yii\helpers\Html;
use yii\bootstrap\ActiveForm;
use yii\captcha\Captcha;
$this->title = 'Книги';
$this->params['breadcrumbs'][] = $this->title;
?>
```
