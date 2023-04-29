# Webpack

<aside>
💡 Webpack의 작동 원리에 대하여 다루고있습니다.
</aside>

</br>

# 👀 Bundler - Webpack

> .js, .sass, css, jpg 등을 하나하나의 모듈로보고 이 모듈들을 배포용으로 병합하고 포장하는 작업을 Bundling이라고 하는데 이러한 번들링 작업을 수행하는 툴을 Bundler라고 한다. 그리고 Bundler 중 가장 인기가 많은 툴이다.

파일의 종류가 많아지면 접속하는 유저의 입장에서 각각 다운로드가 되어 불편하고 오래걸린다. 그래서 수 많은 스크립트를 합치고 css를 합치다보면 브라우저 입장에서 다운로드 할 수가 줄어들기 때문에 속도가 향상된다. 또한 크로스 브라우징 할 때 호환이 안 되는 기능을 컨트롤 할 수 있고 난독화하여 코드를 바꿀 수 있다.
</br></br>

기본 사용 방법 : npm install —save-dev webpack webpack-cli webpack-dev-server html-webpack-plugin

</br>
설치를 하면 package.json에 devDependencies에 저장이 된다.

---

# 💭 webpack.config.json

```jsx
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

//require은 node.js에서 외부의 파일을 불러오는 방법이다.
module.exports = {
  //   entry: "./src/index.js",
  mode: "development",
  entry: {
    index: "./src/index.js",
  },
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "[name].js", //index.js
  },
  devServer: {
    static: "./dist",
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/index.html", //번들전 html
      filename: "./index.html", //번들후 html
      hasg: true, //모든스크립트, css 캐시 무효화
      showErrors: true, //오류 html에 출력
    }),
  ],
};
```

path 기능은 경로를 조금 더 쉽고 다양하게 활용 할 수 있게 활용한 것이다.
</br>

resolve : 합치되, 상위경로와 하위경로로 들어간 주소까지 합치는 함수.

> path: path.resolve(\_\_dirname, "dist")

\_\_dirname/dist 폴더 뒤에 번들이 만들어진다.
</br>
</br>

> HtmlWebpackPlugin은 html을 번들로 만들어준다.

```json
"scripts": {
    "build": "webpack",
    "start": "webpack server --open"
  },
```

package.json에서 build와 start를 수정해서 편하게 터미널에서 npm start 등으로 시작 할 수 있게 한다. npm start로 먼저 확인하고 이상 없으면 npm build를 한다.

---
