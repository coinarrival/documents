# Documents

本项目存放软件的相关文档，使用 gitbook 进行页面管理；gh-pages 进行部署。

## URL

[https://coinarrival.github.io/documents](https://coinarrival.github.io/documents)

## Dependence

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