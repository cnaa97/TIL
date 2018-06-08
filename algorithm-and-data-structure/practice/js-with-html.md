# JS with HTML

```markup
<style>
    #wrap { border: 1px solid red; width: 200px; }
    #wrap div { border: 1px solid red; padding: 10px; margin: 10px; }
    .c-1 { width: 160px; }
    .c-2 { width: 140px; }
    .c-3 { width: 120px; }
    .c-4 { width: 100px; }
</style>

<div id="wrap">
    <div class="c-1">
        Hello
        <div class="c-1-1">Welcome</div>
        <div class="c-1-2">to my</div>
    </div>
    <div class="c-2">
        Home.
        <div class="c-2-1">
            I
            <div class="c-2-1-1">am</div>
        </div>
    </div>
    <div class="c-3">
        Happy
        <div class="c-3-1">Today.</div>
    </div>
    <div class="c-4">
        Thanks
        <div class="c-4-1">Guys!</div>
    </div>
</div>
```

```javascript
// 1. 해당 돔 내 children, childNode를 구분한다.
// 2. 리커시브 알고리즘으로 해당 돔 내 텍스트를 모두 불러온다.
// 3. 특정 범위의 텍스트만 뽑는다.

function printStr(from, to) {
    
    // wrap 내 모든 값을 가져온다.
    // from, to까지 범위를 선택하는데, 어떻게 선택해야할까?

    // 특정 돔을 선택했을 때 해당 돔 아래 텍스트만 가져오는 함수를 만들어본다. 
    // from부터
    let allDiv = $('#wrap').children();
    let fromIndex;
    let toIndex;
    let returnValue = '';
    
    allDiv.each(function(i, o){
        let className = $(o).attr('class');
        if (from.substr(1) === className) {
            fromIndex = i;
        } else if (to.substr(1) === className) {
            toIndex = i;
        }
    })

    allDiv.splice(fromIndex, toIndex).map(function(o){
        returnValue += getText(o);
    });

    return returnValue;
}

let allStr;

function getText(el, str) {
    allStr = str || '';
    const $el = $(el);
    const contents = $el.contents();

    contents.each(function(i, o){
        if ($(this)[0].nodeName === 'DIV') {
            getText(this, allStr);
        } else {
            let text = $(this).text().replace(/\n/gi, "").trim();
            if (text.length > 0) {
                allStr += `${text} `;
            }
        }
    })
    
    return allStr;
}

// `Home. I feel Happy Today.`
// let result = printStr('.c-2', '.c-3');
let result = printStr('.c-2', '.c-3');
console.log(result);
```



