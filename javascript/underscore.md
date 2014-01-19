###underscore总的结构是(function).call(this);
实际上就是在script标签导入进来的时候就把其中的function都运行一遍

	var root = this;  //把当前的对象先用一个root定义起来，在浏览器端就是[window](https://developer.mozilla.org/en-US/docs/Web/API/Window)对象
	var previousUnderscore = root._; //把之前的_的值存起来，之后要覆盖
	var breaker = {};
	var ArrayProto = Array.prototype, ObjProto = Object.prototype, FuncProto = Function.prototype; //一些重要的[prototype](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/URIError/prototype) 
	var
		push             = ArrayProto.push,
		slice            = ArrayProto.slice,
		concat           = ArrayProto.concat,
		toString         = ObjProto.toString,
		hasOwnProperty   = ObjProto.hasOwnProperty; // 把一些重要的方法有个快速链接
	var
	    nativeForEach      = ArrayProto.forEach,
	    nativeMap          = ArrayProto.map,
	    nativeReduce       = ArrayProto.reduce,
	    nativeReduceRight  = ArrayProto.reduceRight,
	    nativeFilter       = ArrayProto.filter,
	    nativeEvery        = ArrayProto.every,
	    nativeSome         = ArrayProto.some,
	    nativeIndexOf      = ArrayProto.indexOf,
	    nativeLastIndexOf  = ArrayProto.lastIndexOf,
	    nativeIsArray      = Array.isArray,
	    nativeKeys         = Object.keys,
	    nativeBind         = FuncProto.bind; // ECMAScript5 native functions
	var _ = function(obj) {
	    if (obj instanceof _) return obj;
	    if (!(this instanceof _)) return new _(obj);
	    this._wrapped = obj;
	};   // 创建一个_对象

	if (typeof exports !== 'undefined') {
	    if (typeof module !== 'undefined' && module.exports) {
	      exports = module.exports = _;
	    }
	    exports._ = _;
	} else {
	    root._ = _;
	} // 如果exports存在(即server端js node，把_赋给exprots), 否则，就是root, 即window object

	_.VERSION = '1.5.2'; 现在的版本号

	