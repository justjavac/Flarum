源项目地址：https://github.com/flarum/core

QQ 交流群：<a target="_blank" href="http://shang.qq.com/wpa/qunwpa?idkey=ce16b9ac4b222fce3102c41fcc39048cba045d1d242bc33ed5e845c1166c138a" title="Flarum交流群">188723593</a>

中文论坛(基于esoTalk)：http://discuss.flarum.org.cn

Live Demo http://demo.flarum.org

--------------------

我是 [Toby Zerner](http://tobyzerner.com)， [esoTalk](http://esotalk.org) 的开发者。
年前，我构建了一个新颖的，轻量级的 esoTalk 论坛的替代者。
esoTalk 非常好，但是它[没有构建在一个可持续发展的基础上](http://bbs.justjavac.com/6)（译注：esoTalk 的底层框架重新发明了轮子）。

**基于此，我们需要一个现代的，优雅的，简洁的，强大的论坛软件，并且易于使用和托管。**
这就是 Flarum。但我是一个全职学生，我没有足够的时间独立完成这个项目。
于是我将采用开放协作的方式来开发 Flarum —— 让全世界的开发者一起开发 Flarum。

![Flarum 截图](https://pbs.twimg.com/media/B7eOB3bCMAE88_f.png:large)

## 安装

**Flarum is currently in development and will be ready to use later this year.** ([Roadmap](http://tobyzerner.com/flarum/)) If you want to give the development version a spin or are interested in contributing, for now you can install Flarum's Vagrant image. An easier installation process will become a priority once Flarum is more stable.

1. Install [Vagrant](https://www.vagrantup.com) and [VirtualBox](https://www.virtualbox.org).
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

Building Flarum is going to be a team effort, and we'd love for you to help! All contributions are welcomed.

### Contributor License Agreement

By contributing your code to Flarum you grant Toby Zerner a non-exclusive, irrevocable, worldwide, royalty-free, sublicenseable, transferable license under all of Your relevant intellectual property rights (including copyright, patent, and any other rights), to use, copy, prepare derivative works of, distribute and publicly perform and display the Contributions on any licensing terms, including without limitation: (a) open source licenses like the MIT license; and (b) binary, proprietary, or commercial licenses. Except for the licenses granted herein, You reserve all right, title, and interest in and to the Contribution.

You confirm that you are able to grant us these rights. You represent that You are legally entitled to grant the above license. If Your employer has rights to intellectual property that You create, You represent that You have received permission to make the Contributions on behalf of that employer, or that Your employer has waived such rights for the Contributions.

You represent that the Contributions are Your original works of authorship, and to Your knowledge, no other person claims, or has the right to claim, any right in any invention or patent related to the Contributions. You also represent that You are not legally obligated, whether by entering into an agreement or otherwise, in any way that conflicts with the terms of this license.

Toby Zerner acknowledges that, except as explicitly described in this Agreement, any Contribution which you provide is on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING, WITHOUT LIMITATION, ANY WARRANTIES OR CONDITIONS OF TITLE, NON-INFRINGEMENT, MERCHANTABILITY, OR FITNESS FOR A PARTICULAR PURPOSE.
