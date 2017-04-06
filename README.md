# live2d-helper.js
Display Live2D models on web page.

Actually, it's a simple package for the Live2D official demo.

## Setup
First, import scripts into your page.

You can [download](http://sites.cybernoids.jp/cubism-sdk2_e/webgl2-1) `live2d.min.js` from offcial website or get it from the `lib` folder.

And include the `live2d-helper.min.js` located on the `dist` folder.

```html
<script src="live2d.min.js"></script>
<script src="live2d-helper.min.js"></script>
```

## Example
```html
<canvas id="glcanvas" width="400" height="600"></canvas>

<script src="live2d.min.js"></script>
<script src="live2d-helper.min.js"></script>
<script type="text/javascript">
    var live2DHelper = new Live2DHelper({canvas: 'glcanvas'});
    
    window.onload = function() {
        var path = "name.model.json";
        live2DHelper.loadModel(path, function(){
            // do something...
        });
    };
</script>
```

## Methods

* `loadModel(modelPath, callback)`
    * `modelPath` - path of model json data
    * `callback` - callback

* `releaseModel(no)`
    * `no` - model index

* `releaseAllModel()` 

```
release all model
```

* `changeModel(newModelPath, callback)`
    * `newModelPath` - new model json data path
    * `callback` - callback

```
the model in bottom of stack release,
and the new model will push in top of stack.

! this function is recommended when you have only ctreated one model.
```

* `setRandomExpression(no)`
    * `no` - model index, default: 0

```
set random expression
```

* `getExpressions(no)`
    * `no` - model index, default: 0

```
return all expression names.
iterate: 
for (var name in live2DHelper.getExpressions()) {
  // ...
}
```

* `setExpression(name, no)`
    * `name` - expression name
    * `no` - model index, default: 0

```
set model expression by name
```

* `startRandomMotion(no)`
    * `no` - model index, default: 0

* `startMotion(namespace, num, no)`
    * `namespace` - motion namespace
    * `num` - motion index
    * `no` - model index, default: 0

* `playSound(path, no)`
    * `path` - sound path
    * `no` - model index, default: 0

```
play sound use Audio DOM
it only works once in FireFox
```

* `playSoundAJAX(path, no)`
    * `path` - sound path
    * `no` - model index, default: 0

```
play sound use AJAX and Web Audio API
it can work in both Chrome and Firefox, but the sound must be played after download
```

## Thanks
[avgjs / pixi-live2d](https://github.com/avgjs/pixi-live2d)

[DotSaikyo / Live2D](https://github.com/DotSaikyo/Live2D)

[kakinuma4ko / WebLive2DMurakumo](https://github.com/kakinuma4ko/WebLive2DMurakumo)


## License
MIT