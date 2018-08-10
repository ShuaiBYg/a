# 快速创建元素
你可以使用以下方法快速创建元素：

<script>
	window.$$ = function(type,obj,position,before){

		var element;
		var other = {
			'frag': 'createDocumentFragment',
        	'text': 'createTextNode' 
		}
		if(other[type]){
			element = document.other[type]();
		}else{
			element = document.createElement(type);
		}
		if(obj){
			for(var i in obj){
				if(typeof obj[i] == 'object'){
					for(var j in obj[i]){
						var box = obj[i];
						element[i][j] = box[j];	
					}
				}else{
					element.setAttribute(i,obj[i]);
				}
			}
		}
		if (position) {
			if(before){
				//insert element before beforeelment
				position.inserBefore(element,before);
			}else{
				position.appendChild(element);
			}
		}
		return element;
	}
</script>
