源项目地址：https://github.com/flarum/core

**来吧，让我们一起构建一个让小伙伴们都惊呆的 PHP 论坛。**

-------------------

QQ 交流群：<a target="_blank" href="http://shang.qq.com/wpa/qunwpa?idkey=ce16b9ac4b222fce3102c41fcc39048cba045d1d242bc33ed5e845c1166c138a" title="Flarum交流群">188723593</a>

中文论坛(基于esoTalk)：http://discuss.flarum.org.cn

--------------------

我是 [Toby Zerner](http://tobyzerner.com)， [esoTalk](http://esotalk.org) 的开发者。
年前，我构建了一个新颖的，轻量级的 esoTalk 论坛的替代者。
esoTalk 非常好，但是它[没有构建在一个可持续发展的基础上](http://bbs.justjavac.com/6)（译注：esoTalk 的底层框架重新发明了轮子）。

**基于此，我们需要一个现代的，优雅的，简洁的，强大的论坛软件，并且易于使用和托管。**
这就是 Flarum。但我是一个全职学生，我没有足够的时间独立完成这个项目。
于是我将采用开放协作的方式来开发 Flarum —— 让全世界的开发者一起开发 Flarum。

## 开发理念

I have a vision for Flarum — one that has grown over years of playing with forums, developing esoTalk, and learning from mistakes. It is captured by the following four points:

- **Modern design.** Beautiful, clean, customizable. Forum design hasn’t evolved with the rest of the web; let's finally bring it up to speed.
- **Unopinionated feature-set.** Every community is different, and forum software should be able to adapt to — rather than define — how a community is run. As such, Flarum will have a lightweight core, and most features will be implemented as optional extensions.
- **High performance.** Flarum should perform well on scales big and small, and on a large range of devices.
- **Sustainable architecture.** Flarum should be built for the future, on a strong foundation which can evolve with the technologies that power it.

Flarum is open-source software released under the [MIT license](https://github.com/flarum/core/blob/master/LICENSE.txt).

## Technology

I've carefully considered which frameworks to use to build Flarum. Here's the reasoning:

### Laravel

PHP remains the most user-friendly language for deploying web scripts, especially on shared hosting. The Laravel framework will allow for rapid development of Flarum’s API, and has a large community which will encourage collaboration and evolution.

### Ember.js

Ember.js is a mature JavaScript framework which will power Flarum’s front-end. Use of a JavaScript framework allows us to build a fast, dynamic interface which feels more like an app than a simple web page.

> Don't like the fact that Flarum is an Ember.js app? Take a look at [FluxBB 2](https://github.com/fluxbb/fluxbb/tree/2.0), which is being developed in a more traditional manner with Laravel.

## Current State

I’ve been working on a prototype for some time in-between my studies. In addition to interface design, most of my time has been spent building out the architecture: making decisions about which frameworks to use, the most effective way to componentize everything, standardizing the API, etc.

You might notice that a lot of the code is a bit of a mess right now. This is because I wanted to get things working on a superficial level in order to record material for the Kickstarter video, and since then I haven't yet had sufficient time to clean it up. Please be aware that the mess is not at all indicative of the standard that we're aiming for!

### 已经完成的

- [x] 基础技术栈 (Laravel 和 Ember)
- [x] 三层架构的 [体系结构](http://discuss.flarum.org.cn/17-flarum-architecture) (core/API/web layers)
- [x] 部分 API (discussion 和 post 的读写)
- [x] Discussion 的列表和初级的搜索功能
- [x] Discussion 详情页和滚动

### What’s Next

The priority at the moment is to build out a lightweight core, and only start building [Extensions](https://github.com/flarum/core/wiki/Extensions) when it is relatively stable. Below is a list of the things to work on immediately, with links to the relevant discussion.

- [ ] 界面重新设计 ([界面设计预览](http://discuss.flarum.org.cn/16-flarum))
- [ ] 升级到 Laravel 5
- [ ] 为 Laravel 和 Ember 设置测试框架 
- [ ] 进一步开发扩展接口 (vi [Extensions](https://github.com/flarum/core/wiki/Extensions))
- [ ] 开发用户认证策略
- [ ] 实现回复主题(discussion)、编辑帖子(post)、创建主题(discussion)
- [ ] 实现编辑主题(discussion)标题
- [ ] 实现删除帖子(post)
- [ ] 实现删除主题(discussion)
- [ ] 设计用户中心界面
- [ ] 设计管理界面
- [ ] 创建通知(notification)系统

For a full list of planned features, see [Features](https://github.com/flarum/core/wiki/Features).

## Installation

Currently Flarum is in its very early stages, and it isn’t pretty. **It is far from usable.** Set it up only if you know what you’re doing, and expect it to break a lot.

1. Make sure you have [Composer](http://getcomposer.org), [ember-cli](http://www.ember-cli.com), and [Bower](http://bower.io) installed globally.
2. Create a new [Laravel 4](http://laravel.com/docs/4.2/quick) project.
3. Clone the Flarum repository into the workbench and install dependencies:
	
	```
	git clone https://github.com/flarum/core.git workbench/flarum/core
	cd workbench/flarum/core
	composer install
	cd ../../..
	php artisan dump-autoload
	```

5. Create a new MySQL database and configure your database details in `app/config/database.php`.
6. Run the Flarum migrations and database seeder to generate dummy data:

	```
	php artisan migrate --bench="flarum/core"
	php artisan db:seed --class="Flarum\Core\Support\Seeders\DatabaseSeeder"
	```

7. Add the Flarum service providers to the `providers` array in `app/config/app.php`:

	```
	'Flarum\Core\CoreServiceProvider',
	'Flarum\Api\ApiServiceProvider',
	'Flarum\Web\WebServiceProvider'
	```

8. Remove the default route in `app/routes.php`.
9. Run the following commands to compile the Ember app:

	```
	cd workbench/flarum/core/ember
	npm install
	bower install
	ember serve --output-path="../public"
	```

10. Visit your Laravel application in a browser.  

	> Note: You must access the Laravel application so that it is at the top level (i.e. not under any sub-directories.) To do this, you can either set your web server's document root to the `public` folder of your application, or you can [configure a virtual host](http://davidwalsh.name/create-virtual-host) pointing to the `public` folder.

If you’re having trouble, **do not** create a new issue — instead, get help on the [Flarum Development Forum](http://discuss.flarum.org) or hop on the IRC channel (#flarum on irc.freenode.net).

## Contributing

Building Flarum is going to be a team effort, and we'd love for you to help! All contributions are welcomed.

### What Can I Do?

- **Contribute code.** Start by becoming familiar with Flarum's source code and its [Architecture](https://github.com/flarum/core/wiki/Architecture). Then have a look at what needs to be done in the list above, and see if there's anything you can help out with. See below for instructions on submitting a Pull Request.

- **Participate in discussion.** Review the [wiki](https://github.com/flarum/core/wiki) and [issues](https://github.com/flarum/core/issues) and contribute your constructive thoughts. We'd also love to hear general feedback on the [Flarum Development Forum](http://discuss.flarum.org), on IRC (#flarum on irc.freenode.net), and on [Twitter](http://twitter.com/flarum).

- **Spread the word.** Know someone who could help out? Please share this project with them!

> In this early stage of development, bug reports won't be particularly helpful, because things will be constantly changing and breaking.

### Process

1. Review the [Flarum Contributor License Agreement](#contributor-license-agreement). ([Why?](https://julien.ponge.org/blog/in-defense-of-contributor-license-agreements/))

2. Install Flarum as detailed in the instructions above. 

3. Create a new branch.

	```
	git checkout -b new-flarum-branch
	```

	> Please implement only one feature/bugfix per branch to keep pull requests clean and focused.

4. Code. 
	- Follow the coding style: [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md). 
	- Include tests and make sure they pass (subject to [#3](https://github.com/flarum/core/issues/3) and [#4](https://github.com/flarum/core/issues/4)).

5. Commit. 
	- Commit messages are **required**. 
	- They should include a short description of the changes on the first line, then a blank line, then more details if necessary. 

6. Clean up. Squash together minor commits.

	```
	git rebase -i
	```

7. Update your branch so that it is based on top of the latest code from the Flarum repository.

	```
	git fetch origin
	git rebase origin/master
	```

8. Fork your repository on GitHub and push to it.

	```
	git remote add mine git@github.com:<your user name>/flarum.git
	git push mine new-flarum-branch
	```

9. Submit a pull request.
	- Go to the Flarum repository you just pushed to (e.g. https://github.com/your-user-name/flarum).
	- Click "Pull Request". 
	- Write your branch name in the branch field. 
	- Click "Update Commit Range". 
	- Ensure that the correct commits and files changes are included. 
	- Fill in a descriptive title and other details about your pull request. 
	- Click "Send pull request".

10. Respond to feedback.
	- We may suggest changes to your code. Maintaining a high standard of code quality is important for the longevity of this project — use it as an opportunity to improve your own skills and learn something new!

### Core Team

Currently the only person on the core development team is Toby Zerner ([@tobscure](http://twitter.com/tobscure)). Over time, judged by display of commitment to the project, and quantity/quality of contributions, I will be looking for more people to join the core development team. Please do not email me asking to be on the core team; rather, demonstrate initiative and commitment to the project, and I will more than likely notice!

### Contributor License Agreement

By contributing your code to Flarum you grant Toby Zerner a non-exclusive, irrevocable, worldwide, royalty-free, sublicenseable, transferable license under all of Your relevant intellectual property rights (including copyright, patent, and any other rights), to use, copy, prepare derivative works of, distribute and publicly perform and display the Contributions on any licensing terms, including without limitation: (a) open source licenses like the MIT license; and (b) binary, proprietary, or commercial licenses. Except for the licenses granted herein, You reserve all right, title, and interest in and to the Contribution.

You confirm that you are able to grant us these rights. You represent that You are legally entitled to grant the above license. If Your employer has rights to intellectual property that You create, You represent that You have received permission to make the Contributions on behalf of that employer, or that Your employer has waived such rights for the Contributions.

You represent that the Contributions are Your original works of authorship, and to Your knowledge, no other person claims, or has the right to claim, any right in any invention or patent related to the Contributions. You also represent that You are not legally obligated, whether by entering into an agreement or otherwise, in any way that conflicts with the terms of this license.

Toby Zerner acknowledges that, except as explicitly described in this Agreement, any Contribution which you provide is on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING, WITHOUT LIMITATION, ANY WARRANTIES OR CONDITIONS OF TITLE, NON-INFRINGEMENT, MERCHANTABILITY, OR FITNESS FOR A PARTICULAR PURPOSE.
