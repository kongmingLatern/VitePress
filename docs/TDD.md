# 1. 什么是 TDD？

TDD：`Test-Driven Development`，(测试驱动开发)，换句话说就是：

> 先编写测试，然后再编写代码，让这些代码能够通过测试，然后以此往复执行。

# 2. 为什么要使用 TDD？

首先，通过 TDD 的形式编写的项目，

- 有着良好的扩展性
- 能够较为容易的检测出错的代码片段
- 阅读性也会大大提高
- 维护成本较低

## 2.1 为什么 TDD 会具有良好的扩展性？

因为上面说过，TDD 的开发思想就是 `测试驱动开发`，我们会先写测试再编写代码，这样的好处在于

- 我们可以根据用户（或个人）的需求对程序进行约束，这样其实可以适当避免先编写代码后可能会在中途忘记某些信息的风险。
- 编写测试遵循着**小步走**：每编写完一块功能就进行单元测试，然后再执行所有的测试（避免修改某些代码后导致其他测试不通过）。

遵循着 小步走 的原则，这样使用 TDD 编写的程序功能就会变得越来越多，而且像这样每次编写完代码就执行测试，就不用担心会影响到之前的功能，所以它具有良好的扩展性。

## 2.2 为什么 TDD 能够容易的检查出 错的代码片段？

上面说了，同样遵循着 小步走 的原则，每次编写新功能的时候假如导致了新测试的失败，那么错误在哪里就十分明显了；或者等你编写新功能的时候会影响到之前的功能，那么就可以通过排查该测试代码，来确保测试是否具有漏洞等。

## 2.3 为什么使用 TDD 会提高阅读性？

在 项目 中，现在通常会使用 `jest` 或者 `vitest` 等测试框架去实现 TDD 的思想

如以下测试

```js
describe('描述信息', () => {
  test('测试的内容，例如 1 + 1 应该为 2', () => {
    expect(1 + 1).toBe(2)
  })
})
```

从这块代码中我们可以很明显的知道这块内容测试的就是 1 + 1 = 2，对于一些较为复杂的测试，可以进行更加具体的描述来提高阅读性，这样方便后续进行扩展。不过，对于一些较为复杂的测试，最好需要进行任务拆分（`Tasking`）

## 2.4 为什么使用 TDD 后维护成本较低？

因为 上述几个原因，所以使用它以后项目的维护成本就会较低。

**扩展**
这里其实还有一种测试是：`BDD`，它是 **集成测试**，而 `TDD` 主要是 **单元测试**

集成测试：就是通过测试把各种功能组合在一起，这个和 TDD 的主要区别在于，这个是**先写代码，再写测试**

# 3. TDD 带来的一些问题

- 测试编写的严谨性，要确保测试的正确性
- 测试编写耗时较长，最好能在开发前梳理好思路
- 对于一些场景来说，测试并不能很好的体现以及编写（就比如 sdk 中的一些异常处理）。
