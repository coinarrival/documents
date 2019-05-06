# Documents

本项目存放软件的相关文档，使用 gitbook 进行页面管理；gh-pages 进行部署。

## URL

[https://coinarrival.github.io/documents](https://coinarrival.github.io/documents)

## Dependence

1. git >= 2.18.1
1. node
1. npm

## Initialization

```bash
npm install -g gitbook-cli
npm install -g gh-pages
```

## Usage

### Page Control

将新增页面的文件名更新到 Summary.md 后，使用 `gitbook init` 命令自动创建页面文件

### Local Serve

`gitbook serve` 可进行本地预览

### Deploy document

```bash
gitbook build
gh-pages -d _book
```

### Q&A

1. `gh-pages -d _book` 出现以下问题：

    ```bash
    fatal: HttpRequestException encountered.
    bash: /dev/tty: No such device or address
    error: failed to execute prompt script (exit code 1)
    fatal: could not read Username for 'https://github.com': Invalid argument
    ```

    - [Solution-1 更改 git 配置](https://github.com/tschaub/gh-pages/issues/230#issuecomment-368868268)
    - [Solution-2 更新 git 版本](https://git-scm.com/downloads)
