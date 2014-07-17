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
 <label class="control-label col-md-2" >�K�X</label>
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
	//�s�W�@�Ӱ϶����Ҫ���
        field1 = new ValidMode();
        //��l�ư�����e�����ҭn�Q���Ҫ����
         //�d�� : field1.valid_Init('�ҭn���Ҫ�Class�W��','���񴣥ܦr��','����LabelCss�˦�','���ҥ��T���ɦ�m');
        field1.valid_Init('valid','�������','color:green;font-family: arial;font-size:large;','./img/green_checkmark_small-1.gif');
        //��HTML��ID���ҥ[�J�ҭn���Ҫ����W��ܪk�H�δ��ܦr��
        //�d�� : field1.AddRegexPatern('ID',regex, '���ܦr��');
        field1.AddRegexPatern('email', /^\w+((-\w+)|(\.\w+))*\@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z]+$/, '�п�J���T���q�l�l��榡');
        field1.AddRegexPatern('phone', /^([0-9]{10,10})$/, '�п�J�Q�X������X');
        field1.AddRegexPatern('password', /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])[0-9a-zA-Z]{8,}$/, '�п�J�ܤ֤K��V�X�Ʀr�^��j�p�g���K�X');
         field1.AddRegexPatern('url',/https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{2,256}\.[a-z]{2,6}\b([-a-zA-Z0-9@:%_\+.~#?&/=]*)/, '�п�JURL');
        //��l����L��J�۰�����
        field1.KeyPressInit();


        //�s�W�t�@�Ӱ϶����Ҫ���
        field2 = new ValidMode();    
        field2.valid_Init('valid2','�������','color:red;font-family: arial;font-size:large;','./img/checkmark_small.gif');
        field2.AddRegexPatern('email2', /^\w+((-\w+)|(\.\w+))*\@[A-Za-z0-9]+((\.|-)[A-Za-z0-9]+)*\.[A-Za-z]+$/, '�п�J���T���q�l�l��榡');
        field2.AddRegexPatern('phone2', /^\d+$/, 'Pleas enter the phone number');
        field2.KeyPressInit();
    });

	 function SaveClick(){
	 	 //�������ҵ{�� ���ŦX���ҳW�h�^��false �ŦX�^��true
        var pass = field1.runValid();
         if (pass === true) {
         	alert('Pass!!!');
         }
	 }
	 function Cancel(){
	 	//�M�����Ҵ���
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