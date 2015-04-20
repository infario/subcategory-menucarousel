installation

1. un pack the zip and copy the subcategory-menucarousel.xml to vqmod/xml


2. open the style sheet catalog\view\theme\<your Theme>\stylesheet\stylesheet.css find below code

#menu > ul > li > div {
	display: none;
	background: #FFFFFF;
	position: absolute;
	z-index: 5;
	padding: 5px;
	border: 1px solid #000000;
	-webkit-border-radius: 0px 0px 5px 5px;
	-moz-border-radius: 0px 0px 5px 5px;
	-khtml-border-radius: 0px 0px 5px 5px;
	border-radius: 0px 0px 5px 5px;
	background: url('../image/menu.png');
}

and replace with below code

#menu > ul > li > div {

position: absolute;
left: 5px;
z-index: 5;
border: 2px solid #d6d6d6;
-webkit-border-radius: 0px 0px 5px 5px;
background: #fff;	
width: 992px;
box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.32);
-webkit-box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.32);
-moz-box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.32);
-ms-box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.32);
box-shadow: inset 0px 4px 62px rgba(0, 0, 0, 0.08);
-webkit-box-shadow: inset 0px 4px 62px rgba(0, 0, 0, 0.08);
-moz-box-shadow: inset 0px 4px 62px rgba(0, 0, 0, 0.08);
-ms-box-shadow: inset 0px 4px 62px rgba(0, 0, 0, 0.08);
box-sizing: border-box;
-wekbit-box-sizing: border-box;
-moz-box-sizing: border-box;
-ms-box-sizing: border-box;
min-height: 100px;
z-index: 99999;
}

3. open the script file \catalog\view\javascript\common.js

find the below code section 

$('#menu ul > li > a + div').each(function(index, element) {
		// IE6 & IE7 Fixes
		if ($.browser.msie && ($.browser.version == 7 || $.browser.version == 6)) {
			var category = $(element).find('a');
			var columns = $(element).find('ul').length;
			
			$(element).css('width', (columns * 143) + 'px');
			$(element).find('ul').css('float', 'left');
		}		
		
		var menu = $('#menu').offset();
		var dropdown = $(this).parent().offset();
		
		i = (dropdown.left + $(this).outerWidth()) - (menu.left + $('#menu').outerWidth());
		
		if (i > 0) {
			$(this).css('margin-left', '-' + (i + 5) + 'px');
		}
	});
	
and replace with below code 

$('#menu ul > li > a + div').each(function(index, element) {
		// IE6 & IE7 Fixes
		if ($.browser.msie && ($.browser.version == 7 || $.browser.version == 6)) {
			var category = $(element).find('a');
			var columns = $(element).find('ul').length;
			
			$(element).css('width', (columns * 143) + 'px');
			$(element).find('ul').css('float', 'left');
		}		
		
		var menu = $('#menu').offset();
		var dropdown = $(this).parent().offset();
		
		var menuWidth = $('#menu').width();
		$(this).width(menuWidth);

		
		i = (dropdown.left + $(this).outerWidth()) - (menu.left + $('#menu').outerWidth());
		
		if (i > 0) {
			$(this).css('margin-left', '-' + (i + 9) + 'px');
		}
	});
	
	