# 异步编程

### async/await
```html
<div>
    <div class="light" id="red"></div>
    <div class="light" id="yellow"></div>
    <div class="light" id="green"></div>
</div>

<style>
    .light {
        display: inline-block;
        width: 100px;
        height: 100px;
        border: 1px solid black;
        border-radius: 100%;
    }
</style>

<script>

    var lighting = (color, time) => new Promise( resolve => {
        var light = document.getElementById(color)
        light.style.background = color
        setTimeout(()=>{
            light.style.background = "white"
            resolve()
        }, time * 1000)
    })

    var main = async() => {
        while(true){
            await lighting("red", 10)
            await lighting("yellow", 2)
            await lighting("green", 5)
        }
    }

    main()

</script>
```

### Generate
```html
<div>
    <div class="light" id="red"></div>
    <div class="light" id="yellow"></div>
    <div class="light" id="green"></div>
</div>

<style>
    .light {
        display: inline-block;
        width: 100px;
        height: 100px;
        border: 1px solid black;
        border-radius: 100%;
    }
</style>

<script>

  var lighting = (color, time) =>  {
        var light = document.getElementById(color)
        light.style.background = color
        setTimeout(()=>{
            light.style.background = "white"
            app.next()
        }, time * 1000)
    }

    function* main() {
        while(true){
            yield lighting("red", 10);
            yield lighting("yellow", 2);
            yield lighting("green", 5);
        }
    }

    var app = main()
    app.next()

</script>
```