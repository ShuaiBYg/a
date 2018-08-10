# 快速创建元素-$$
你可以使用以下方法快速创建元素：

    //创建的元素类型,样式对象{"class":"style"},追加的地方，（非必填）追加到某个元素前面
    window.$$ = function(type,obj,position,before){
        var element;
        var other = {
            'frag': 'createDocumentFragment',
            'text': 'createTextNode' 
        }
        //创建文档碎片节点和文本要做特殊处理
        //添加多个dom元素时，先将元素append到DocumentFragment中，最后统一将DocumentFragment添加到页面。 该做法可以减少页面渲染dom元素的次数。
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
