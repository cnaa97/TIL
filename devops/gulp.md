# gulp

_IE 대응을 위해 바벨을 적용할 일이 생겼는데, 이왕 사용하게 된 걸, gulp를 이용해서 스크립트를 es5 문법으로 변경하고, uglify까지 함께 적용하기로 했다._

gulp는 자바스크립트 빌드 자동화 툴이다. 

### 설치

`npm install -g gulp`

`npm init` 

`npm install -save-dev gulp gulp-util`

gulp에서 ES6 문법을 사용하기 위해 필요한 모듈 설치

`npm install --save-dev babel-core babel-preset-es2015`

`.babelrc` 파일 생성

{% code-tabs %}
{% code-tabs-item title=".babelrc" %}
```text
{
  "presets": ["es2015"]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

gulpfile.babel.js 작성

{% code-tabs %}
{% code-tabs-item title="gulpfile.babel.js" %}
```javascript
import gulp from 'gulp';
import gutil from 'gulp-util';
import babel from 'gulp-babel'; // babel을 사용하기 위한 플러그인

import uglify from 'gulp-uglify';
import cleanCSS from 'gulp-clean-css';
import del from 'del';

const DIR = {
    SRC: 'assets',
    DEST: 'dist'
};

const SRC = {
    JS: DIR.SRC + '/js/*.js',
    CSS: DIR.SRC + '/style/*.css',
};

gulp.task('clean', () => {
    return del.sync([DIR.DEST]); // dist 디렉토리 하위 비우기
});

gulp.task('js', () => {
    return gulp.src(SRC.JS)
        .pipe(babel({ // babel을 사용해서 js 파일 변환
            presets: ['es2015']
        }))
        .pipe(uglify()) // minify 
        .pipe(gulp.dest(DIR.DEST));
});

gulp.task('css', () => {
    return gulp.src(SRC.CSS)
           .pipe(cleanCSS({compatibility: 'ie8'})) // css minify
           .pipe(gulp.dest(DIR.DEST));
});

// 특정 디렉토리 하위에 변화를 감지해서 변경사항 반영
gulp.task('watch', () => { 
    gulp.watch(SRC.JS, ['js']);
    gulp.watch(SRC.CSS, ['css']);
});


gulp.task('default', ['clean', 'js', 'css', 'watch'], () => {
    gutil.log('Gulp is running');
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

스크립트 실행

```bash
# 특정 태스크만 실행시키려면 뒤에 태스크명 추가 입력
# gulp css

gulp
```



