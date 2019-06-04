# more-form

## 实例   
在input中输入，过1s后才显示输入值，渲染数据过多出现卡顿情况     
![Image text](http://ps5shq58f.bkt.clouddn.com/form-ori.gif)

## 优化后
Vue.prototype._update中的this.$el是从组件的根部遍历开始的，原因是data数据都是被劫持的，当data数据被改变后，会触发subs中所有watcher调用update方法，由于data数据量太多，update多次造成卡顿，解决办法是缩小当前组件绑定的数据量，拆分组件   
![Image text](http://ps5shq58f.bkt.clouddn.com/form-ref.gif)
