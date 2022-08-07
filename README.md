# Book
book

###  (一) vue +  eslint  +  prettier  + husky

#### 1， 没有.git 的执行 git init  生成。
#### 2, 安装必要package，运行如下命令行：
```
npm install -D prettier husky@4.3.8 lint-staged eslint-config-prettier eslint-plugin-prettier @commitlint/config-conventional @commitlint/cli
```
### 3, 在package.json 中加入如下代码：

```
  "lint-staged": {
    "src/**/*.{js,json,css,vue}": [
      "prettier --write",
      "eslint --fix",
      "git add"
    ]
  }
```
### 4, 在根目录下创建eslintrc.js 文件，并在文件内写入如下内容：
```
/* eslint-disable no-dupe-keys */
/* eslint-disable no-undef */
// .eslintrc.js
module.exports = {
  extends: ['plugin:vue/strongly-recommended', 'plugin:prettier/recommended'],
  rules: {
    'prettier/prettier': 'off',

    'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off',

    /**
     * 代码中可能的错误或逻辑错误
     */
    'no-cond-assign': ['error', 'always'], // 禁止条件表达式中出现赋值操作符
    'no-constant-condition': ['error', { checkLoops: true }], // 禁止在条件中使用常量表达式
    'no-control-regex': ['error'], // 禁止在正则表达式中使用控制字符
    'no-debugger': ['error'], // 禁用 debugger
    'no-dupe-args': ['error'], // 禁止 function 定义中出现重名参数
    'no-dupe-keys': ['error'], // 禁止对象字面量中出现重复的 key
    'no-duplicate-case': ['error'], // 禁止出现重复的 case 标签
    'no-empty': ['error', { allowEmptyCatch: true }], // 禁止出现空语句块
    'no-empty-character-class': ['error'], // 禁止在正则表达式中使用空字符集
    'no-ex-assign': ['error'], // 禁止对 catch 子句的参数重新赋值
    'no-extra-boolean-cast': ['error'], // 禁止不必要的布尔转换
    'no-extra-semi': ['error'], // 禁止不必要的分号
    'no-func-assign': ['warn'], // 禁止对 function 声明重新赋值
    'no-inner-declarations': ['error'], // 禁止在嵌套的块中出现变量声明或 function 声明
    'no-invalid-regexp': ['error', { allowConstructorFlags: [] }], // 禁止 RegExp 构造函数中存在无效的正则表达式字符串
    'no-irregular-whitespace': ['error'], // 禁止在字符串和注释之外不规则的空白
    'no-obj-calls': ['error'], // 禁止把全局对象作为函数调用
    'no-regex-spaces': ['error'], // 禁止正则表达式字面量中出现多个空格
    'no-sparse-arrays': ['error'], // 禁用稀疏数组
    'no-unexpected-multiline': ['error'], // 禁止出现令人困惑的多行表达式
    'no-unsafe-finally': ['error'], // 禁止在 finally 语句块中出现控制流语句
    'no-unsafe-negation': ['error'], // 禁止对关系运算符的左操作数使用否定操作符
    'use-isnan': ['error'], // 要求使用 isNaN() 检查 NaN

    /**
     * 最佳实践
     */
    'default-case': ['error'], // 要求 switch 语句中有 default 分支
    'dot-notation': ['error'], // 强制尽可能地使用点号
    eqeqeq: ['warn'], // 要求使用 === 和 !==
    'no-caller': ['error'], // 禁用 arguments.caller 或 arguments.callee
    'no-case-declarations': ['error'], // 不允许在 case 子句中使用词法声明
    'no-empty-function': ['error'], // 禁止出现空函数
    'no-empty-pattern': ['error'], // 禁止使用空解构模式
    'no-eval': ['error'], // 禁用 eval()
    'no-global-assign': ['error'], // 禁止对原生对象或只读的全局对象进行赋值
    'no-magic-numbers': ['error', { ignoreArrayIndexes: true }], // 禁用魔术数字
    'no-redeclare': ['error', { builtinGlobals: true }], // 禁止重新声明变量
    'no-self-assign': ['error', { props: true }], // 禁止自我赋值
    'no-unused-labels': ['error'], // 禁用出现未使用过的标
    'no-useless-escape': ['error'], // 禁用不必要的转义字符
    radix: ['error'], // 强制在parseInt()使用基数参数

    /**
     * 变量声明
     */
    'no-delete-var': ['error'], // 禁止删除变量
    'no-undef': ['error'], // 禁用未声明的变量，除非它们在 /*global */ 注释中被提到
    'no-unused-vars': ['error'], // 禁止出现未使用过的变量
    'no-use-before-define': ['error'], // 禁止在变量定义之前使用它们

    /**
     * ECMAScript 6
     */
    'arrow-spacing': ['error', { before: true, after: true }], // 强制箭头函数的箭头前后使用一致的空格
    'no-var': ['error'], // 要求使用 let 或 const 而不是 var
    'object-shorthand': ['error', 'always'], // 要求或禁止对象字面量中方法和属性使用简写语法
    'prefer-arrow-callback': ['error', { allowNamedFunctions: false }], // 要求回调函数使用箭头函数
  },
};

```

5, 在根目录下创建prettier.config.js 文件，并写入如下内容：5, 在根目录下创建prettier.config.js 文件，并写入如下内容：
```
// prettier.config.js
/* eslint-disable no-dupe-keys */
/* eslint-disable no-undef */
module.exports = {
  printWidth: 80, // 每行代码长度（默认80）
  tabWidth: 2, // 每个tab相当于多少个空格（默认2）
  useTabs: false, // 是否使用tab进行缩进（默认false）
  singleQuote: true, // 使用单引号（默认false）
  semi: true, // 声明结尾使用分号(默认true)
  trailingComma: 'all', // 多行使用拖尾逗号（默认none）
  bracketSpacing: true, // 对象字面量的大括号间使用空格（默认true）
  jsxBracketSameLine: false, // 多行JSX中的>放置在最后一行的结尾，而不是另起一行（默认false）
  arrowParens: 'avoid', // 只有一个参数的箭头函数的参数是否带圆括号（默认avoid）
};

```
6, 根目录下创建　.huskyrc 文件并写入如下内容：
```
{
  "hooks": {
    "pre-commit": "lint-staged",
    "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
  }
}
```
7,  根目录下创建.commitlintrc.js 文件，写入如下内容：
```
module.exports = {
    extends: ["@commitlint/config-conventional"],
    rules: {
        'type-enum': [2, 'always', [
          'upd', 'feat', 'fix', 'refactor', 'docs', 'chore', 'style', 'revert'
         ]],
        'type-case': [0],
        'type-empty': [0],
        'scope-empty': [0],
        'scope-case': [0],
        'subject-full-stop': [0, 'never'],
        'subject-case': [0, 'never'],
        'header-max-length': [0, 'always', 72]
      }
  };
```
Thanks to :

1 https://juejin.cn/post/6844903661726875656

2 https://www.npmjs.com/package/@commitlint/config-conventional

3 https://juejin.cn/post/6972130175681036295

4 https://www.npmjs.com/package/@commitlint/config-conventional

( 二) [国内安装Howbrew](https://zhuanlan.zhihu.com/p/111014448)

文档汇总：[浏览器资源加载原理](https://juejin.cn/post/6844903545016156174)

