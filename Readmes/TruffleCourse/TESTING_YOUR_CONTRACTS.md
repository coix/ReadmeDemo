测试智能合约
===========

## 框架

Truffle 提供了一套标准的自动化测试框架，这就使得测试智能合约变得简单了。
这个框架允许你以两种不同的方式编写简单和可管理的测试:

- 使用 JavaScript 编写，从外部来执行你的合约，就像应用一样。
- 使用 Solidity 编写，进阶的外部执行合约，适用于 bare-to-the-metal（实在不知道怎么翻译） 场景。

两种测试方法都有各自的优缺点，下面两个板块将会详细讨论。

## 测试脚本位置

所有测测试脚本文件应该在 ```./test/``` 文件夹下。 ```truffle``` 只会运行 
```.js .es .es6 .jsx .sol``` 这些后缀的脚本，其他文件都会被忽略。

## 命令

运行所有测试脚本：

```bash
$ truffle test
```

指定特定文件运行测试脚本：

```bash
$ truffle test ./path/to/test/file.js
```

## 净室环境

Truffle 提供了一个净室环境来运行你的测试脚本。在针对Ganache或Truffle开发运行测试时，
Truffle 将使用高级的快照特性，以确保测试文件不会彼此共享状态。当与其他 Ethereum 客户端(如go-ethereum)运行时，
Truffle 将在每个测试文件开始时重新部署所有迁移，以确保您有一组新的合约要测试。

## 速度和可靠性方面的考虑

在运行测试脚本的时候 ```Truffle Develop``` 和 ```Ganache``` 都比其他客户端要快。
此外，它们还包含一些特殊的特性，Truffle利用这些特性将测试运行时间提高了近90%。
作为一个通用的工作流，我们建议您在正常的开发和测试过程中使用 Ganache 或 Truffle Develop ，
然后在您准备部署到 live 或生产网络时，对 go-ethereum 或其他 Ethereum 客户端进行一次测试。
