源项目地址：https://github.com/flarum/flarum

中文语言包：https://github.com/justjavac/flarum-i18n-zh

QQ 交流群：<a target="_blank" href="http://shang.qq.com/wpa/qunwpa?idkey=ce16b9ac4b222fce3102c41fcc39048cba045d1d242bc33ed5e845c1166c138a" title="Flarum交流群">188723593</a>

微信群：

![微信群二维码](images/weixin_group.png)

中文开发者论坛：http://discuss.flarum.org.cn

Live Demo http://demo.flarum.org

--------------------

我是 [Toby Zerner](http://tobyzerner.com)， [esoTalk](http://esotalk.org) 的开发者。
年前，我构建了一个新颖的，轻量级的 esoTalk 论坛的替代者。
esoTalk 非常好，但是它[没有构建在一个可持续发展的基础上](http://bbs.justjavac.com/6)（译注：esoTalk 的底层框架重新发明了轮子）。

**基于此，我们需要一个现代的，优雅的，简洁的，强大的论坛软件，并且易于使用和托管。**
这就是 Flarum。但我是一个全职学生，我没有足够的时间独立完成这个项目。
于是我将采用开放协作的方式来开发 Flarum —— 让全世界的开发者一起开发 Flarum。

## 安装

**Flarum is currently in development and will be ready to use later this year.** ([Roadmap](http://tobyzerner.com/flarum/)) If you want to give the development version a spin or are interested in contributing, for now you can install Flarum's Vagrant image. An easier installation process will become a priority once Flarum is more stable.

1. 安装 [Vagrant](https://www.vagrantup.com) 和 [VirtualBox](https://www.virtualbox.org).
2. Clone this repository and set up the Vagrant box:

  ```sh
  git clone --recursive https://github.com/flarum/flarum.git
  cd flarum
  vagrant up
  ```

3. Add an entry to your /etc/hosts file:

  ```192.168.29.29 flarum.dev```

4. Visit flarum.dev in a browser.

## Contributing

Interested in contributing to Flarum? Read the [Contribution Guide](https://github.com/flarum/flarum/blob/master/CONTRIBUTING.md)!

Bug reports should go in [flarum/core](https://github.com/flarum/core/issues) or the [relevant extension repository](https://github.com/flarum).

### 核心团队

- Toby Zerner ([esoTalk](http://esotalk.org), [@tobscure](http://twitter.com/tobscure))
- Franz Liedke ([FluxBB](http://fluxbb.org), [@franzliedke](http://twitter.com/franzliedke))
