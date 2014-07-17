Simple Validation
===================================  

How to build your Simple Validation
----------------------------
### Firstly, include Jquery and SimpleValid in your web page.
```
<script src="./js/jquery-1.10.2.min.js"></script>
<script src="./js/SimpleValid.js"></script>

```

### Add a class name to your input element for validation to set it is required, try something like 'valid'.

```
 <div id="field1">
 <label class="control-label col-md-2" >密碼</label>
 <input class="text-box single-line valid" id="password" type="password">
 </div>

```
### Then new a validation object in your javascript code and init it, you must give it a validation class name, required tip, tip label's css style and image for check correct.
```
field1 = new ValidMode();
field1.valid_Init('Class Name(valid)','required tip','Label Css style','check correct image');

```
### Run your validation. 
```
 var pass = field1.runValid();
         if (pass === true) {
         	alert('Pass!!!');
         }

```
### You can add specific regular expression to validate your input distinctly.
```
field1.AddRegexPatern('element ID(password)',regular expression, 'Tip words');

```
### Also, you can init the auto validation to detect your input.

```
field1.KeyPressInit();

```
### Clear all tip words.

```
field1.ClearValid();

```
### Sample Code
```
<script type="text/javascript">
	 $(document).ready(function () {
	//新增一個區塊驗證物件
        field1 = new ValidMode();
        //初始化偵測當前頁面所要被驗證的欄位
         //範例 : field1.valid_Init('所要驗證的Class名稱','必填提示字串','提示LabelCss樣式','驗證正確圖檔位置');
        field1.valid_Init('valid','必填欄位','color:green;font-family: arial;font-size:large;','./img/green_checkmark_small-1.gif');
        //依HTML的ID標籤加入所要驗證的正規表示法以及提示字串
        //範例 : field1.AddRegexPatern('ID',regex, '提示字串');
        field1.AddRegexPatern('email', /^\w+((-\w+)|(\.\w+))*\@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z]+$/, '請輸入正確的電子郵件格式');
        field1.AddRegexPatern('phone', /^([0-9]{10,10})$/, '請輸入十碼手機號碼');
        field1.AddRegexPatern('password', /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])[0-9a-zA-Z]{8,}$/, '請輸入至少八位混合數字英文大小寫的密碼');
         field1.AddRegexPatern('url',/https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{2,256}\.[a-z]{2,6}\b([-a-zA-Z0-9@:%_\+.~#?&/=]*)/, '請輸入URL');
        //初始化鍵盤輸入自動驗證
        field1.KeyPressInit();


        //新增另一個區塊驗證物件
        field2 = new ValidMode();    
        field2.valid_Init('valid2','必填欄位','color:red;font-family: arial;font-size:large;','./img/checkmark_small.gif');
        field2.AddRegexPatern('email2', /^\w+((-\w+)|(\.\w+))*\@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z]+$/, '請輸入正確的電子郵件格式');
        field2.AddRegexPatern('phone2', /^\d+$/, 'Pleas enter the phone number');
        field2.KeyPressInit();
    });

	 function SaveClick(){
	 	 //執行驗證程序 不符合驗證規則回傳false 符合回傳true
        var pass = field1.runValid();
         if (pass === true) {
         	alert('Pass!!!');
         }
	 }
	 function Cancel(){
	 	//清除驗證提示
	 	field1.ClearValid();
	 }

	 function SaveClick2(){
        var pass = field2.runValid();
         if (pass === true) {
         	alert('Pass!!!');
         }
	 }

	 function Cancel2(){
	 	field2.ClearValid();
	 }
</script>
```