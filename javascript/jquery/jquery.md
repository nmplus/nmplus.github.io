# Jquery

[JQuery] 다른 라이브러리로부터 jQuery 보호하기 

 

jQuery도 많고 많은 라이브러리중에 하나일뿐입니다. 그러다 보니 이런저런 라이브러리들과 같이 사용하다보면 jQuery의 내부에서 사용하는 글로벌 객체 예를들면 $ 가 있겠죠? 아무튼 글로벌한 무언가가 다른 라이브러리와 충돌이 발생하여 문제가 발생할 수가 있습니다. 예를들면 prototype.js 나 MooTools 같은 라이브러리가 될 것 같습니다. 

jQuery에서는  $ 를 jQuery를 사용할수 있는 일종의 매개체로써 사용을 하고 있습니다. 물론 $ 는 글로벌하게 정의가 된 상태입니다. 그러다 보니 만약에 다른 라이브러리에서 $ 를 자체적으로 재정의를 한다면 우리가 jQuery에서 기대하는 기능을 아무것도 사용하지 못하게 됩니다. 

일단은 이건 조금 문제가 있어 보입니다. 그래서 이러한 충돌을 막기 위해서는 jQuery를 no-conflict  모드로 사용해 줘야 합니다. 이는 페이지가 로드되고 jQuery가 페이지에서 무언가를 하기 전에 설정이 되어야합니다. 

 

<!-- Putting jQuery into no-conflict mode. --> 

<script src="prototype.js"></script> 

<script src="jquery.js"></script> 

<script> 

  

var $j = jQuery.noConflict(); 

// $j is now an alias to the jQuery function; creating the new alias is optional. 

  

$j(document).ready(function() { 

    $j( "div" ).hide(); 

}); 

  

// The $ variable now has the prototype meaning, which is a shortcut for 

// document.getElementById(). mainDiv below is a DOM element, not a jQuery object. 

window.onload = function() { 

    var mainDiv = $( "main" ); 

} 

  

</script> 

 

예를 들면 이런 형태가 될것같습니다. 위의 코드의 경우에는 $ 가 더 이상 jQuery에서의 역할을 하지 않습니다. 대신 $j 가 그역활을 대신할것입니다. 또는 jQuery라는 풀네임으로 사용해도 됩니다. 

그런데 위와 같은 방법이 또다른 혼란을 불러 일으킬수 있을가능성이 있다고 판단이 되거나 또는 귀찮을 경우에는 jQuery(document).ready() 함수에 $ 를 인자로 전달하면 됩니다. 

<!-- Another way to put jQuery into no-conflict mode. --> 

<script src="prototype.js"></script> 

<script src="jquery.js"></script> 

<script> 

  

jQuery.noConflict(); 

  

jQuery( document ).ready(function( $ ) { 

    // You can use the locally-scoped $ in here as an alias to jQuery. 

    $( "div" ).hide(); 

}); 

  

// The $ variable in the global scope has the prototype.js meaning. 

window.onload = function(){ 

    var mainDiv = $( "main" ); 

} 

  

</script> 

 

 

이렇게 말이죠! 아마도 이게 가장 이상적인 해결책이 아닐까 생각합니다. 

 

또 다른 방법은 그냥 jQuery를 사용할 때는 그냥 jQuery라는 풀네임으로 사용하는 것입니다.  

 

정리를 하면 총 3가지의 방법으로 jQuery를 다른 라이브러리로부터 충돌없이 사용할수 있는데 

첫번째가 새로운 이름으로 선언을 하는 것 

 

<script src="prototype.js"></script> 

<script src="jquery.js"></script> 

<script> 

  

// Give $ back to prototype.js; create new alias to jQuery. 

var $jq = jQuery.noConflict(); 

  

</script> 

 

두번째가 대부분의 jQuery의 라이브러리에서 채택하고 있는 패턴으로 실행함수로 감싸는 방법입니다. 

<!-- Using the $ inside an immediately-invoked function expression. --> 

<script src="prototype.js"></script> 

<script src="jquery.js"></script> 

<script> 

  

jQuery.noConflict(); 

  

(function( $ ) { 

    // Your jQuery code here, using the $ 

})( jQuery ); 

  

</script> 

 

마지막으로 $를 인자로 전달하는 방법입니다. 

<script src="jquery.js"></script> 

<script src="prototype.js"></script> 

<script> 

  

jQuery(document).ready(function( $ ) { 

    // Your jQuery code here, using $ to refer to jQuery. 

}); 

  

</script> 

 

또는  

 

<script src="jquery.js"></script> 

<script src="prototype.js"></script> 

<script> 

  

jQuery(function($){ 

    // Your jQuery code here, using the $ 

}); 

  

 

이상 다른 라이브러리와의 충돌없이 jQuery를 사용하는 방법이었습니다. 
