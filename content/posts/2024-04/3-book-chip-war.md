---
title: "边读边想简中版得删成筛子吧——读《Chip War》"
author: 椒盐豆豉
type: post
date: 2024-04-11T18:38:00-07:00
url: /book-chip-war/
categories:
  - 喜欢就买
tags:
  - reading
  - 导读
  - tech
booktoc: false
bookComments: true
image: https://media.douchi.space/douchi/media_attachments/files/112/255/605/181/513/566/original/89037b748644fa6f.png
imageDes: "MidJourney prompt: electronics war --ar 16:9. 如果直接 prompt chip war 的话就会生成出一堆赌场筹码（也叫 chip），现阶段 AI 替代人类真的还仍需努力 🤣"
---

此书简中版（`芯片战争`）几乎是跟英文原版同步发行的（差了半年），本来我对此类话题不感兴趣，但是看到象友吐槽难以想象简中版要怎么删便引起了兴趣，遂去年底开始读，断断续续几个月前阵子终于在旅途中的飞机上读完了。作为一本芯片业的流水史，能摘出来的干货还是不少的，没记笔记等于没读，这里也整理一下笔记吧。

{{< neodb "https://neodb.social/book/2Q9qj6JlefSqkF2xamwGAu" 8 "https://amzn.to/43SfkUR" "断断续续读了三个月终于读完了，全程想法是“这书简中版得删成啥德行啊”。读更古早一点的芯片科技史还挺有波澜壮阔的感觉，具体技术和工程上的突破过程也很有意思，再更当代就感觉随着科技进步变成 incremental & iteration 少了很多上古大神神仙打架高魔（？）的感觉。" >}}

<!--more-->

以下中文笔记为我个人翻译概括，没有跟官方的简中版校对过。

>vacuum tubes glowed like lightbulbs, they attracted insects, requiring regular “debugging” by their engineers. Also like lightbulbs, vacuum tubes often burned out

引出了现代常用术语 debug 的源头热知识：真空管会发光，所以会吸引昆虫，工程师需要经常“除虫”。此外像灯泡一样真空管也会经常烧毁。

> science alone wasn’t enough to build the chip industry. The spread of semiconductors was enabled as much by clever manufacturing techniques as academic physics. Universities like MIT and Stanford played a crucial role in developing knowledge about semiconductors, but the chip industry only took off because graduates of these institutions spent years tweaking production processes to make mass manufacturing possible. It was engineering and intuition, as much as scientific theorizing, that turned a Bell Labs patent into a world-changing industry.

光靠科学并不足以构建芯片产业。芯片产业的蓬勃发展依赖巧妙的制造工艺不亚于以来物理学术眼睛。MIT 和斯坦福等大学在发展半导体知识方面至关重要，但芯片工业爆发更依赖于这些学生毕业后花了大量时间调整优化生产工艺来使大规模生产成为现实。

> Selling R&D to the government was like taking your venture capital and putting it into a savings account,” Noyce declared. “Venturing is venturing; you want to take the risk.”

把研发卖给政府就像是把风投的钱放进存款账户，风投是喜欢冒险的。—— Noyce（Fairchild 及 Intel 的创始人之一）

> Defense contractors thought about chips mostly as a product that could replace older electronics in all the military’s systems. At Fairchild, Noyce and Moore were already dreaming of personal computers and mobile phones

国防合约把芯片看作是一种军事系统里的旧电子产品的替代品。而在 Fairchild, Noyce 和摩尔早就开始梦想进军个人电脑和移动电话。

> Shokin’s “copy it” strategy was fundamentally flawed, however. Copying worked in building nuclear weapons, because the U.S. and the USSR built only tens of thousands of nukes over the entire Cold War. In the U.S., however, TI and Fairchild were already learning how to mass-produce chips. The key to scaling production was reliability, a challenge that American chipmakers like Morris Chang and Andy Grove fixated on during the 1960s. Unlike their Soviet counterparts, they could draw on the expertise of other companies making advanced optics, chemicals, purified materials, and other production machinery. If no American companies could help, Fairchild and TI could turn to Germany, France, or Britain, each of which had advanced industries of their own.

Alexander Shokin （负责苏联半导体工业的官员）的抄袭策略从根本上有缺陷。亦步亦趋在生产核武器上能成功，但德州仪器和 Fairchild 早就在研究如何大规模生产芯片了。扩大生产规模的关键是可靠性，一个美国的芯片生产者如 Morris Chang（張忠謀，TSMC 创始人）和 Andy Grove（Intel 第三任 CEO）在 1960 年代全力以赴的问题。不像苏联的对手，他们可以利用其它公司在先进光学、化学、材料提纯和其它生产工具上的专业知识。如果美国公司不够，还能找德国、法国、英国等各自拥有先进工业的国家。

> Chip firms hired women because they could be paid lower wages and were less likely than men to demand better working conditions. Production managers also believed women’s smaller hands made them better at assembling and testing finished semiconductors.

芯片公司因为工资较低和更少要求改善工作环境而招聘女性。生产经理也相信女性手更小更适合组装和测试半导体。

> Fairchild was the first semiconductor firm to offshore assembly in Asia, but Texas Instruments, Motorola, and others quickly followed. Within a decade, almost all U.S. chipmakers had foreign assembly facilities. Sporck began looking beyond Hong Kong. The city’s 25-cent hourly wages were only a tenth of American wages but were among the highest in Asia. In the mid-1960s, Taiwanese workers made 19 cents an hour, Malaysians 15 cents, Singaporeans 11 cents, and South Koreans only a dime.

Farichild 是第一家在亚洲组装半导体的公司，但德州仪器、摩托罗拉和其它公司很快跟进了。10 年之内，几乎所有的美国芯片商都拥有国外组装工厂。Sporck（Charles Sporck, CEO of National Semiconductor）首先看中了香港，当时香港 25 分的时薪仅为美国的十分之一，却是亚洲最高的。1960 年代中期，台湾工人时薪 19 美分，马拉西亚 15 美分，新加坡 11 美分，韩国则只有 10 分。

> We had union problems in Silicon Valley,” Sporck noted. “We never had any union problems in the Orient.

Sporck 观察道：硅谷有工会问题。东方从来都没有工会问题。

> Many people would later describe the mainland-born Chang as “returning” to Taiwan, but 1968 was the first time he stepped foot on the island, having lived in the U.S. since fleeing the Communist takeover of China. Two of Chang’s PhD classmates at Stanford were from Taiwan, however, and they convinced him the island had a favorable business climate and that wages would stay low.

很多人都会用“回到”这个词来描述在中国大陆出生的 Morris Chang，但实际上 1968 年是他从共产党占领大陆逃到美国之后第一次踏上台湾岛。两位他的斯坦福台湾 PhD 同学说服了他台湾的商业条件更好，工资也会保持低廉。

> Noyce and Moore abandoned Fairchild as quickly as they’d left Shockley’s startup a decade earlier, and founded Intel, which stood for Integrated Electronics. In their vision, transistors would become the cheapest product ever produced, but the world would consume trillions and trillions of them. Humans would be empowered by semiconductors while becoming fundamentally dependent on them. Even as the world was being wired to the United States, America’s internal circuitry was changing. The industrial era was ending. Expertise in etching transistors into silicon would now shape the world’s economy. Small California towns like Palo Alto and Mountain View were poised to become new centers of global power.

Noyce 和摩尔像十年前抛弃 Shockley 的 startup 一样抛弃了 Fairchild，创立了 Intel，集成电器的缩写。他们认为半导体会成为史上最廉价的产品，但会有数以万亿计的需求量。半导体会使人类更强大也更依赖它们。在世界中心向美国转移的同时，美国内部的气候也产生了变化。工业时代正在结束，在硅上蚀刻导体会成为塑造世界经济的决定因素。Palo Alto 和 Mountain View 这种加州小镇已经在成为世界中心的道路上前进。

> In the early 1960s, it had been possible to claim the Pentagon had created Silicon Valley. In the decade since, the tables had turned. The U.S. military lost the war in Vietnam, but the chip industry won the peace that followed, binding the rest of Asia, from Singapore to Taiwan to Japan, more closely to the U.S. via rapidly expanding investment links and supply chains. The entire world was more tightly connected to America’s innovation infrastructure, and even adversaries like the USSR spent their time copying U.S. chips and chipmaking tools. Meanwhile, the chip industry had catalyzed an array of new weapons systems that were remaking how the U.S. military would fight future wars. American power was being recast. Now the entire nation depended on Silicon Valley’s success

1960 年代早期，可以说是五角大楼缔造了硅谷。在其后的十年中，风向则完全变了。美国军队输了越南战争，但芯片行业赢得了随后而来的和平年代，将从新加坡到台湾到日本的亚洲其它地区用投资和供应链跟美国更紧密地结合起来。整个世界都与美国的创新产业更紧密结合起来，甚至像苏联一样的敌对方都在花时间抄袭美国芯片设计和制作工具。与此同时，芯片工业也生产了一系列新武器系统，完全改变了美军未来的作战方式。美国国力现在依赖硅谷的成功。

> Sony’s research director, the famed physicist Makoto Kikuchi, told an American journalist that Japan had fewer geniuses than America, a country with “outstanding elites.” But America also had “a long tail” of people “with less than normal intelligence,” Kikuchi argued, explaining why Japan was better at mass manufacturing.

索尼研发总监，著名物理学家菊池誠告诉美国记者，日本的天才少于精英辈出的美国，但美国也有一大批“拖后腿”的“低智”人群，因此日本更擅长大规模生产。

> In the 1970s, Silicon Valley firms had forgotten about the government as they replaced defense contracts with civilian computer and calculator markets. In the 1980s, they crawled sheepishly back to Washington. After their dinner at Ming’s, Sanders, Noyce, and Sporck joined other CEOs to create the Semiconductor Industry Association to lobby Washington to support the industry

1970 年代，硅谷的公司把政府抛诸脑后，用民用电脑和计算器市场替换了国防合约。1980 年代，它们乖乖爬回华盛顿跪舔。Sanders, Noyce 和 Sporck 再一次晚餐后与其它的 CEO 一起建立了美国半导体行业协会来游说政府补助芯片产业。

> America had long seen itself as Japan’s teacher, but Morita thought America had lessons to learn as it struggled with a growing trade deficit and the crisis in its high-tech industries. “The United States has been busy creating lawyers,” Morita lectured, while Japan has “been busier creating engineers.” 

美国很久以来都以日本的老师自视，但盛田昭夫（索尼共同创始人）认为正在芯片危机中挣扎的美国还有很多要学。“美国忙着培训律师”，盛田昭夫说，“而日本忙着生产工程师”。

> Conway was a brilliant computer scientist, but anyone who spoke with her discovered a mind that glistened with insights from diverse fields, astronomy to anthropology to historical philosophy. She had arrived at Xerox in 1973 in “stealth mode,” she explained, following being fired from IBM in 1968 after undergoing a gender transition.

Lynn Conway（美国电脑、电器科学家、跨性别权益活动家）是一位杰出的科学家，但也拥有广泛的其它领域知识。她在 1968 年 IBM 发现了她进行变性手术后将其开除后 1973 年偷偷来到 Xerox。（这里补充一下[之前写过的介绍](https://t.me/mtfront/3001)：Lynn Conway 对大规模集成电路设计起到的关键作用的部分，才发现原来这么早（1960 - 80 年代）就有跨性别女性在科技行业风口浪尖了！她之前本来在 IBM 工作，发明了 generalized dynamic instruction handling，也是最早进行荷尔蒙疗法的跨性别人士之一。结果 IBM 1968 年发现之后开除了她（？），2020 年才正式道歉。）

> One popular Soviet joke from the 1980s recounted a Kremlin official who declared proudly, “Comrade, we have built the world’s biggest microprocessor!”

1980 年一个流行苏联笑话：一位克林姆林宫官员骄傲地宣称：同志们，我们制造了世界上最大的微处理器！

> The Soviet Union barely had a consumer market, so it produced only a fraction of the chips built in the West. One Soviet source estimated that Japan alone spent eight times as much on capital investment in microelectronics as the USSR

苏联几乎没有消费市场，所以其芯片产量只占西方的零头。一个苏联消息源估计光日本微电子上的投入就是苏联的八倍。

> CEOs of Japan’s memory chip producers couldn’t bring themselves to stop building new chip fabs, even if they weren’t profitable. “If you start worrying” about overinvestment, one Hitachi executive admitted, “you can’t sleep at night.” So long as banks kept lending, it was easier for CEOs to keep spending than to admit they had no path to profitability.

即便不能盈利，日本记忆芯片产业的 CEO 们完全无法停歇地建造新的芯片制造厂。“如果你开始担心过度投资”，一位日立的高管承认，“你就会夜不能寐。”所以只要银行还肯借钱，CEO 们继续花钱总比承认他们无法盈利更容易。

> When the integrated circuit was invented, China had many of the ingredients that helped Japan, Taiwan, and South Korea attract American semiconductor investment, like a vast, low-cost workforce and a well-educated scientific elite. However, after seizing power in 1949, the Communists looked at foreign connections with suspicion. For someone like Morris Chang, returning to China after finishing his studies at Stanford would have meant certain poverty and possible imprisonment or death. Many of the best graduates from China’s universities before the revolution ended up working in Taiwan or in California, building the electronics capabilities of the PRC’s primary rivals.

集成电路刚被发明的时候，中国也有很多像日本、台湾、韩国一样吸引了美国半导体投资的元素，如大量低廉的劳动力和受过良好教育的科技精英。但是在 1949 年获取政权后，共产党不信任外国势力。像 Morris Chang 一样在斯坦福留学之后如果回到中国将面临不可避免的贫穷和很有可能被监禁乃至死亡。许多革命前中国最好的高校毕业生最后去了台湾或加州工作，为中华人民共和国的主要敌对势力贡献知识。（好奇简中版这章是不是得全删掉）

> Just as Mao was sending China’s small set of skilled workers to the countryside for socialist reeducation, the chip industry in Taiwan, South Korea, and across Southeast Asia was pulling peasants from the countryside and giving them good jobs at manufacturing plants.

当毛泽东把中国的技术工作者人送去上山下乡的时候，台湾、韩国和东南亚的芯片产业正在把农民从乡下吸引到芯片制造产业。

> The Cultural Revolution began to wane as Mao’s health declined in the early 1970s. Communist Party leaders eventually called scientists back from the countryside. They tried picking up the pieces in their labs. But China’s chip industry, which had lagged far behind Silicon Valley before the Cultural Revolution, was now far behind China’s neighbors, too. During the decade in which China had descended into revolutionary chaos, Intel had invented microprocessors, while Japan had grabbed a large share of the global DRAM market. China accomplished nothing beyond harassing its smartest citizens. By the mid-1970s, therefore, its chip industry was in a disastrous state. “Out of every 1,000 semiconductors we produce, only one is up to standard,” one party leader complained in 1975. “So much is being wasted.”

文化大革命在 1970 年代早期毛泽东的健康状况每况日下的时候开始消退。共产党领导人们把科学家从乡下召回，试图在实验室重操旧业。但中国的芯片产业即便在文化大革命之前也落后于硅谷，现在更是也远远落后于其邻国。在文化大革命动乱的十年间，Intel 发明了微处理器，日本占领了全球 DRAM 市场很大份额，中国则只让其最聪明的公民们受罪。到 1970 年代中期，中国的芯片产业惨不忍睹。“我们每生产的 1000 个半导体中只有 1 个符合标准”，一位共产党领导在 1975 年抱怨道，“剩下的都浪费了。”

> Just a handful of years after Intel turned down the iPhone contract, Apple was making more money in smartphones than Intel was selling PC processors

在 Intel 拒绝了 iPhone 合约之后的几年，苹果靠卖智能手机赚了比 Intel 卖 PC 处理器更多的钱。

> A fixation on hitting short-term margin targets began to replace long-term technology leadership. The shift in power from engineers to managers accelerated this process. Otellini, Intel’s CEO from 2005 to 2013, admitted he turned down the contract to build iPhone chips because he worried about the financial implications. A fixation on profit margins seeped deep into the firm—its hiring decisions, its product road maps, and its R&D processes. The company’s leaders were simply more focused on engineering the company’s balance sheet than its transistors. “It had the technology, it had the people,” one former finance executive at Intel reminisced. “It just didn’t want to take the margin hit.”

Intel 开始追求短期利益而不是长期的技术领先。权力从工程师转移到管理者加速了这一过程。Intel 2005 到 2013 年的 CEO Otellini 承认他因为担心经济上的无利可图而拒绝了 iPhone 的芯片合约。追求利润植入了公司的每个角落——招聘方向，产品路线，研发过程。公司的领导们更关心优化公司的账簿而不是半导体。“我们有技术，我们有人才”，一位前 Intel 财务高管回忆道，“我们只是不愿意亏钱。”

> The biggest change, however, wasn’t simply new types of chips. By making possible mobile phones, advanced graphics, and parallel processing, fabless firms enabled entirely new types of computing.

（无厂半导体公司）最大的改变不只是新型的芯片，而是使移动电话、先进图像处理和并行处理成为可能，带来了全新的计算形态。

> For many years, each generation of manufacturing technology was named after the length of the transistor’s gate, the part of the silicon chip whose conductivity would be turned on and off, creating and interrupting the circuit. The 180nm node was pioneered in 1999, followed by 130nm, 90nm, 65nm, and 45nm, with each generation shrinking transistors enough to make it possible to cram roughly twice as many in the same area. This reduced power consumption per transistor.

许多年以来，每一代的生产科技被以其晶体闸（通过开关控制导电性的部分）的长度来命名。1999 年 180nm 被生产，紧接着是 130nm, 90nm, 65nm 和 45nm。每一代的大小缩减使得在同样的面积上挤进更多的晶体成为可能，也减少了耗能。 

> Smartphones and PCs are both assembled largely in China with high-value components mostly designed in the U.S., Europe, Japan, or Korea. For PCs, most processors come from Intel and are produced at one of the company’s fabs in the U.S., Ireland, or Israel. Smartphones are different. They’re stuffed full of chips, not only the main processor (which Apple designs itself)

很多智能手机和电脑都在中国组装，高价值的部件由美国、欧洲、日本或韩国设计。PC 的处理器由 Intel 在美国设计，其美国、爱尔兰或以色列的工厂制造。智能手机不像 PC 一样只有主要芯片（Apple 自己设计），而是有许多不同芯片。(如通讯等)

> Today, no company besides TSMC has the skill or the production capacity to build the chips Apple needs. So the text etched onto the back of each iPhone—“Designed by Apple in California. Assembled in China”—is highly misleading. The iPhone’s most irreplaceable components are indeed designed in California and assembled in China. But they can only be made in Taiwan.

如今，TSMC 成为唯一一家有技术和生产力能制造苹果需要芯片的制造厂。所以刻在每个 iPhone 背面的那行字——“Designed by Apple in California. Assembled in China“ 很有误导性。iPhone 最不可或缺的部分确实是在加州设计中国组装的，但只能被台湾制造。

> If the mirrors in an EUV system were scaled to the size of Germany, the company said, their biggest irregularities would be a tenth of a millimeter. To direct EUV light with precision, they must be held perfectly still, requiring mechanics and sensors so exact that Zeiss boasted they could be used to aim a laser to hit a golf ball as far away as the moon

如果 EUV（极紫外光刻）设备里的镜子放大成德国的大小，其中最大的误差也只有 1/10 毫米大。要精确控制机紫外光光线，它们必须完全静止，所需要的机制和传感器是如此精确以至于蔡司声称该设备可以从地球行射出一道精确击中月球上高尔夫球的激光。

> There are no moving parts in a chip, unless you count the electrons zipping around inside.

芯片中没有移动的部件，除非你算上电子。（所以很可靠）

> ASML’s EUV tools weren’t really Dutch, though they were largely assembled in the Netherlands. Crucial components came from Cymer in California and Zeiss and Trumpf in Germany. And even these German firms relied on critical pieces of U.S.-produced equipment. The point is that, rather than a single country being able to claim pride of ownership regarding these miraculous tools, they are the product of many countries. A tool with hundreds of thousands of parts has many fathers.

ASML（荷兰阿斯麦公司）的 EUV 工具并不是荷兰生产，但大多数是在荷兰组装的。关键部件来自加州的 Cymer，德国的蔡司以及 Trumpf。即使这些德国公司也依赖美国生产的关键部件。总而言之，并不是单一国家能声称拥有这种伟大的工具，它其实是多国产物。一个拥有成百上千部件的工具拥有成百上千的父亲。

> Because manufacturing tools account for much of the cost of an advanced fab, keeping the equipment operating is crucial for profitability. In the U.S., Chiang said, if something broke at 1 a.m., the engineer would fix it the next morning. At TSMC, they’d fix it by 2 a.m.

生产工具占的成本太大，以至于保持它们运行是盈利的关键。蒋尚义（Morris Change 的继任 TSMC CEO）说，如果凌晨 1 点有东西出了问题，美国的工程师会第二天修复。在 TSMC，凌晨 2 点就会修复。

> Since the 1980s, Intel has specialized in a type of chip called a CPU, a central processing unit, of which a microprocessor in a PC is one example. These are the chips that serve as the “brain” in a computer or data center. They are general-purpose workhorses, equally capable of opening a web browser or running Microsoft Excel. They can conduct many different types of calculations, which makes them versatile, but they do these calculations serially, one after another. It’s possible to run any AI algorithm on a general-purpose CPU, but the scale of computation required for AI makes using CPUs prohibitively expensive

从 1980 年代以来，Intel 就专攻 CPU。这是电脑或者数据中心的“大脑“。这些是通用的工具，既能开浏览器和也能运行 Excel。它们可以进行多种运算，比较全能。但它们只能按顺序完成任务。AI 算法也能在通用处理器上运行，但规模之大使得在 CPU 上运行 AI 算法很昂贵。

> Because AI workloads often require running the same calculation repeatedly, using different data each time, finding a way to customize chips for AI algorithms is crucial to making them economically viable.

AI 计算通常需要用不同的数据进行同样的运算多次，因此定制芯片对于优化成本至关重要。

> GPUs, by contrast, are designed to run multiple iterations of the same calculation at once. This type of “parallel processing,” it soon became clear, had uses beyond controlling pixels of images in computer games. It could also train AI systems efficiently

与 CPU 相比，GPU 则是被设计来多次进行同种运算。这种“并行处理”很快就被发现不只是对计算游戏中图像的像素有用，也能更高效地训练 AI。

> No country has been more successful than China at harnessing the digital world for authoritarian purposes

在为威权目的驯化数字世界这件事上，没有国家比中国更成功。

> When it came to artificial intelligence, the country was one of the world’s two AI Superpowers, according to a widely discussed book by Kai-Fu Lee, former head of Google China. Beijing built a twenty-first-century fusion of AI and authoritarianism, maximizing use of surveillance technology. But even the surveillance systems that track China’s dissidents and its ethnic minorities rely on chips from American companies like Intel and Nvidia. All of China’s most important technology rests on a fragile foundation of imported silicon.

前 Google 中国负责人李开复的书声称，在 AI 方向上，中国是世界上仅有的两个 AI 超级大国。北京利用监控科技创造了一种 21 世纪的 AI 和威权主义混合体。但即便是这种追踪中国异议者和少数民族的监控系统也高度依赖美国公司如 Intel 和 Nvidia 的设备。所有中国最重要的科技都依靠着脆弱的进口芯片。

> When Japan, Taiwan, and South Korea wanted to break into the complex and high-value portions of the chip industry, they poured capital into their semiconductor companies, organizing government investment but also pressing private banks to lend. Second, they tried to lure home their scientists and engineers who’d been trained at U.S. universities and worked in Silicon Valley. Third, they forged partnerships with foreign firms but required them to transfer technology or train local workers. Fourth, they played foreigners off each other, taking advantage of competition between Silicon Valley firms

当日本、台湾和韩国试图进军芯片产业高价值的部分时，它们都向半导体公司投入了大量资金，既有政府资金也有向私有银行施压借贷。其次，它们尝试吸引它们国家美国留学硅谷工作的科学家和工程师回国工作。第三，它们与外国企业达成协议，要求转移技术和培训当地工人。最后，它们用硅谷公司之间以及美国与日本之间的竞争获取最有利的合约。

> China was disadvantaged, however, by the government’s desire not to build connections with Silicon Valley, but to break free of it

中国政府并不想与硅谷合作，而想与其脱钩，这使中国站在劣势地位。

> Lee built Samsung from a trader of dried fish into a tech company churning out some of the world’s most advanced processor and memory chips by relying on three strategies. First, assiduously cultivate political relationships to garner favorable regulation and cheap capital. Second, identify products pioneered in the West and Japan and learn to build them at equivalent quality and lower cost. Third, globalize relentlessly, not only to seek new customers but also to learn by competing with the world’s best companies. Executing these strategies made Samsung one of the world’s biggest companies, achieving revenues equivalent to 10 percent of South Korea’s entire GDP.

李秉喆将三星一手从卖鱼干的公司建立成世界上最先进的处理和记忆芯片之一的公司，依赖如下三个策略：1. 建立政治关系获取偏向性政策和低成本资金。2. 寻找西方和日本的先进产品，用更低的成本造出同样质量的产品。3. 全力全球化，不止是全球化的顾客也与全球最先进的公司竞争学习。这三个策略使三星成为世界上最大的公司之一，营收占韩国总 GDP 的 10%。

> Ren Zhengfei’s business model has been fundamentally different from Alibaba’s or Tencent’s. He’s taken concepts pioneered abroad, produced quality versions at lower cost, and sold them to the world, grabbing international market share from international rivals. This business model made Samsung’s founders rich and put the company at the center of the world’s tech ecosystem. Until very recently, Huawei seemed to be on the same path.

任正非的商业模式与阿里巴巴和腾讯完全不同。他从国外获取先进理念，生产优质但更廉价的产品，然后销向世界，占据国际市场。三星用这种策略站在世界科技生态的中心，直到最近，华为也走在同样的道路上。

> Theft of intellectual property may well have benefitted the company, but it can’t explain its success. No quantity of intellectual property or trade secrets is enough to build a business as big as Huawei. The company has developed efficient manufacturing processes that have driven down costs and built products that customers see as high-quality. Huawei’s spending on R&D, meanwhile, is world leading. The company spends several times more on R&D than other Chinese tech firms. Its roughly $15 billion annual R&D budget is paralleled by only a handful of firms, including tech companies like Google and Amazon, pharmaceutical companies like Merck, and carmakers like Daimler or Volkswagen

知识产权盗窃或许帮助了华为，但不能完全解释其成功。只靠知识产权和商业机密是不可能铸就华为这么大的公司的。它研发了高效的生产流程，为顾客生产高质量低成本的产品。华为在研发上的投入也领先世界，超过其它中国科技公司多倍。它每年 150 亿美金左右的研发成本在世界上只有少数公司可以匹敌，如 Google，Amazon，制药公司 Merck，汽车公司 Daimler 或 Volkswagen。

> The scale of state support for an ostensibly private firm has raised red flags, especially in the United States.

对一家表面上是私企的公司大量的国家支持引起了美国的警觉。

> Huawei executive Ken Hu’s argument to a U.S. congressional inquiry that Ren Zhengfei’s membership in the Chinese Communist Party was just like how “some American businessmen are Democrat or Republican,” sounded to U.S. analysts like willful obfuscation of the Communist Party’s role in the company’s governance. Nevertheless, the thesis that Huawei was purpose built by the Chinese state has never had strong evidence behind it.

华为高管 Ken Hu 认为美国国会对任正非党籍的调查就像“一些美国商人是民主党或共和党人”一样，但美国的分析师认为这是混淆视听刻意降低共产党对华为的控制力。无论如何，没有强力证据表明华为是中国政府有意建立的。

> Just as Moore’s Law has let us pack more transistors onto chips, there’s been a steady increase in the number of 1s and 0s flying to and from cell phones via radio waves. 2G phones could send picture texts; 3G phones opened websites; and 4G made it possible to stream video from almost anywhere. 5G will provide a similar leap forward.

随着摩尔定律指引我们将更多晶体管装进芯片，也有更多的 0 和 1 以点播的形式进出手机。2G 手机可以发送图片短信，3G 手机可以打开网站，4G 使几乎随时随地串留视频成为可能。5G 也会带来类似的进步。

> Faster networks capable of carrying more data won’t simply let existing phones run faster—they’ll change the way we think about mobile computing. In the age of 1G networks, cell phones were too expensive for most people to own. With 2G networks, we came to assume that phones could send text messages as well as voice. Today, we expect phones and tablets to have almost all the features of PCs. As it becomes possible to send even more data over cell networks, we’ll connect ever more devices to the cell network. The more devices we have, the more data they’ll produce, which will require more processing power to make sense of.

更快能传输更多数据的网络并不会只让现有的手机变得更快——它们会改变我们看待移动计算的方式。1G 时代，手机对大多数人而言都过于昂贵。2G 时代，手机可以发短信打电话。现在，手机和平板拥有电脑的绝大多数功能。当我们能通过移动网络传输更多数据时，我们也会将更多的设备接入网络。设备越多，生产的数据越多，也就需要更多处理能力。

> Huawei looked likely to play a bigger role in the construction of 5G networks than any other company, overtaking Sweden’s Ericcson and Finland’s Nokia, the only other main producers of the equipment on cell towers.

华为比其它公司更有可能成为 5G 网络建设的主力，超过瑞典的爱立信和芬兰的诺基亚，世界上剩下仅有能生产信号塔设备的公司。

> If the trends of the late 2010s were projected forward, by 2030 China’s chip industry might rival Silicon Valley for influence. This wouldn’t simply disrupt tech firms and trade flows. It would also reset the balance of military power.

按 2010 年代晚期的趋势持续发展，到 2030 年时中国的芯片产业影响可能能与硅谷匹敌。这不仅仅会影响科技公司和贸易，也会改变世界军事力量的平衡。

> Three companies dominate the world’s market for DRAM chips today, Micron and its two Korean rivals, Samsung and SK Hynix. Taiwanese firms spent billions trying to break into the DRAM business in the 1990s and 2000s but never managed to establish profitable businesses. The DRAM market requires economies of scale, so it’s difficult for small producers to be price competitive

三家公司统治着世界 DRAM 芯片的市场：Micron 和其两家韩国对手三星和 SK Hynix。台湾公司从 90 年代以来耗费数十亿试图打入 DRAM 市场但从未成功盈利。DRAM 市场依赖规模效应，所以小生产商很难定价得有竞争力。

> A Fujian court ruled that Micron was responsible for violating UMC and Jinhua’s patents—patents that had been filed using material stolen from Micron. To “remedy” the situation, Fuzhou Intermediate People’s Court banned Micron from selling twenty-six products in China, the company’s biggest market.

一个福建法院判决 Micron 侵犯了 UMC 和 Jinhua 的专利——用从 Micron 盗取的材料申请的专利。进一步巩固战果，福州中级人民法院禁止 Micron 向中国——Micron 的最大市场——销售 26 种产品。

> U.S. companies like Applied Materials, Lam Research, and KLA are part of a small oligopoly of companies that produce irreplaceable machinery, like the tools that deposit microscopically thin layers of materials on silicon wafers or recognize nanometer-scale defects. Without this machinery—much of it still built in the U.S.—it’s impossible to produce advanced semiconductors. Only Japan has companies producing some comparable machinery, so if Tokyo and Washington agreed, they could make it impossible for any firm, in any country, to make advanced chips

像 Applied Materials, Lam Research 和 KLA 一样的美国公司是生产不可取代器材的少数寡头垄断公司，如沉积极薄的材料层在硅片上或识别纳米级的缺陷。没有这些很大一部分仍在美国制造的工具就不可能生产先进半导体。只有日本有公司能生产类似设备，所以如果美国和日本达成共识，它们可以使世界上任何公司或国家无法生产先进芯片。

> The point was less that Huawei was directly supporting China’s military than that the company was advancing China’s overall level of chip design and microelectronics know-how. The more advanced electronics the country produced, the more cutting-edge chips it would buy, and the more the world’s semiconductor ecosystem would rely on China, at the expense of the United States. Moreover, targeting China’s highest-profile tech firm would send a message worldwide, warning other countries to prepare to take sides. Hobbling Huawei’s rise became a fixation of the administration.

与其说是华为只接受中国军方控制，不如说是华为在推进中国整体的芯片设计和微电子水平。中国生产越多的先进电子产品，越需要购买更多的先进芯片，世界的半导体生态就越依赖中国，得罪美国。更进一步，针对中国的风口浪尖科技公司会向世界释放出准备好选边站的警示。美国政府下定决心阻止华为发展。

> Except for hospitals and grocery stores, almost everything was shut. Except for one facility, that is. Yangzte Memory Technologies Corporation (YMTC), based in Wuhan, is China’s leading producer of NAND memory, a type of chip that’s ubiquitous in consumer devices from smartphones to USB memory sticks. There are five companies that make competitive NAND chips today; none are headquartered in China. Many industry experts, however, think that of all types of chips, China’s best chance at achieving world-class manufacturing capabilities is in NAND production

（武汉）除了医院和超市，几乎所有地方都关门了。除了长江存储（YMTC）。它是中国 NAND 记忆芯片的领军生产者，从智能手机到 U 盘都需要。世界上还有其它 5 家公司生产 NAND 芯片，没有一家总部在中国。许多业界专家认为在所有芯片类型中，中国最有可能取得 NAND 芯片生产的领先地位。

> So great is China’s government support for YMTC that even during the COVID lockdown it was allowed to

中国政府对 YMTC 的支持力度之大，以至于即便是 COVID 封城期间，YMTC 也被允许继续开工。

> it’s clear that billions of dollars have been wasted in China on semiconductor projects that are either hopelessly unrealistic or, like HSMC, blatant frauds. If China’s Sputnik moment inspires more state-backed semiconductor programs like these, the country won’t be on a path to technological independence

很明显，数十亿美金被浪费在不切实际的项目或者像 HSMC 一样的诈骗上。如果中国的 Sputnik 时刻（1957 年苏联发射首颗卫星，Sputnik moment 被用来形容一个国家或社会突然意识到它需要追赶别的国家的进步）只是产生了更多这样的国家投资的半导体项目，那中国很难达成科技独立。

> In addition to working with emerging architectures, China’s also focusing on older process technology to build logic chips. Smartphones and data centers require the most cutting-edge chips, but cars and other consumer devices often use older process technology, which is sufficiently powerful and far cheaper

除了投入新架构之外，中国也着力在用旧技术制造逻辑芯片。智能手机和数据中心需要最多最先进的芯片，但汽车和其它民用设备经常用旧的处理设备也足够，还成本更低。

> The Biden administration and most of the media interpreted the chip shortage as a supply chain problem. The White House commissioned a 250-page report on supply chain vulnerabilities that focused on semiconductors. However, the semiconductor shortage wasn’t primarily caused by issues in the chip supply chain. There were some supply disruptions, like COVID lockdowns in Malaysia, which impacted semiconductor packaging operations there. But the world produced more chips in 2021 than ever before—over 1.1 trillion semiconductor devices, according to research firm IC Insights. This was a 13 percent increase compared to 2020. The semiconductor shortage is mostly a story of demand growth rather than supply issues. It’s driven by new PCs, 5G phones, AI-enabled data centers—and, ultimately, our insatiable demand for computing power

拜登政府和大多数媒体认为芯片短缺是供应链问题。白宫发布了 250 页的关于半导体供应链薄弱环节的报告。但是半导体短缺并不主要是芯片供应链造成的。确实有一些供应链受影响，如马来西亚的 COVID lockdown 影响了半导体封装。但据研究机构 IC insights 称， 2021 年全世界生产了有史以来最多的半导体设备——超过 1.1 万亿，与 2020 年相比增加了 13%。半导体短缺更大的原因是需求增加而不是供给问题——新电脑，5G 手机，AI 数据中心……简而言之，我们对计算力的需求。

> In a couple days, absent immediate U.S. and Japanese aid, Chinese air and missile forces could probably disarm key Taiwanese military assets—airfields, radar facilities, communications hubs, and the like—without severely impacting the island’s productive capacity. TSMC’s chairman is certainly right that no one wants to “disrupt” the semiconductor supply chains that crisscross the Taiwan Strait. But both Washington and Beijing would like more control over them

几天之内，美国和日本还没来得及增援前，中国的空军和导弹可以在不影响台湾生产力的前提下破坏台湾的军事设施——机场、雷达、通讯中心等等。TSMC 主席说得很对：没有人想要打断半导体供应链。但美国和中国都想要更好地控制它。

> The idea that China would simply destroy TSMC’s fabs out of spite doesn’t make sense, because China would suffer as much as anyone, especially since the U.S. and its friends would still have access to Intel’s and Samsung’s chip fabs. Nor has it ever been realistic that Chinese forces could invade and straightforwardly seize TSMC’s facilities. They’d soon discover that crucial materials and software updates for irreplaceable tools must be acquired from the U.S., Japan, and other countries. Moreover, if China were to invade, it’s unlikely to capture all TSMC employees. If China did, it would only take a handful of angry engineers to sabotage the entire operation.

中国摧毁 TSMC 工厂的想法完全不合理，因为中国也会受到像所有人一样的损失，尤其是在美国和其它盟国仍有 Intel 和三星的芯片工厂的前提下。中国强行武力占领 TSMC 的工厂也不现实，因为很快他们就会发现关键材料和工具的软件更新必须从美国、日本等其它国家获取。更重要的是，就算中国入侵，也不可能俘获所有的 TSMC 员工。就算他们想要，只需要少数愤怒的员工就能破坏整个生产线。

> However, it’s easy to imagine a way that an accident, like a collision in air or at sea, could spiral into a disastrous war that neither side wants. It’s also perfectly reasonable to think China might conclude that military pressure without a full-scale invasion could decisively undermine America’s implicit security guarantee and fatally demoralize Taiwan. Beijing knows that Taiwan’s defense strategy is to fight long enough for the U.S. and Japan to arrive and help

然而，空中或海域上的意外摩擦却有可能升级成为两方都不愿意看到的灾难性战争。合理推断，中国会认定军事威胁而不是全面入侵更能削弱美国并不明确的安全保障和致命打击台湾的士气。中国知道台湾的防御策略是尽可能抵抗得够久，等待美国和日本的帮助。

> A blockade is an act of war, but no one would want to shoot first. If the U.S. did nothing, the impact on Taiwan’s will to fight could be devastating. If China then demanded that TSMC restart chip fabrication for Huawei and other Chinese companies, or even to transfer critical personnel and know-how to the mainland, would Taiwan be able to say no

封锁是引战行为，但没人愿意开第一枪。如果美国什么也不错，台湾的继续斗争意愿将会受到致命打击。如果中国随后要求 TSMC 重新为华为和其它中国公司制造芯片，或者转移关键技术人员和经验到大陆，台湾能说不吗？

> Analysts uniformly agree that the military balance in the Strait has shifted decisively in China’s direction. Long gone are the days, as during the 1996 Taiwan Strait crisis, that the U.S. could simply sail an entire aircraft carrier battlegroup through the Strait to force Beijing to stand down. Now such an operation would be fraught with risk for the U.S. warships. Today Chinese missiles threaten not only U.S. ships around Taiwan but also bases as far away as Guam and Japan. The stronger the PLA gets, the less likely the U.S. is to risk war to defend Taiwan. If China were to try a campaign of limited military pressure on Taiwan, it’s more likely than ever that the U.S. might look at the correlation of forces and conclude that pushing back isn’t worth the risk

分析一致认为台湾海峡军事平衡逐渐向中国方向倾斜。1996 年台湾海峡危机美国派航母和战斗机在海峡进军强迫中国就范的日子已经一去不复返。如今同样的行动可能会把美国的战舰置于风险。现在中国的导弹不仅能威胁到美国在台湾附近的战舰，还能抵达关岛和日本。如果中国真的试图对台湾施加军事压力，美国比以往更有可能决定不值得冒险而袖手旁观。

> Every company that’s invested on either side of the Taiwan Strait, from Apple to Huawei to TSMC, is implicitly betting on peace. Trillions of dollars are invested in firms and facilities within easy missile shot of the Taiwan Strait, from Hong Kong to Hsinchu. The world’s chip industry, as well as the assembly of all the electronic goods chips enable, depends more on the Taiwan Strait and the South China coast than on any other chunk of the world’s territory except Silicon Valley.

双方每个向台湾海峡两侧投资了的公司，从苹果到华为再到台积电，都在押注和平。数以万亿美元计的资金都投入在了台湾海峡导弹覆盖范围内，从香港到新竹。台湾海峡和中国南海边境是世界上芯片产业和电子产品仅次于硅谷最被依赖的地区。

> Much of Silicon Valley’s knowledge could be easily relocated in case of war or earthquake. This was tested during the pandemic, when almost all the region’s workers were told to sit at home. Big tech firms’ profits even went up. If Facebook’s fancy headquarters were to sink into the San Andreas Fault, the company might barely notice. If TSMC’s fabs were to slip into the Chelungpu Fault, whose movement caused Taiwan’s last big earthquake in 1999, the reverberations would shake the global economy. It would only take a handful of explosions, deliberate or accidental, to cause comparable damage. Some back-of-the-envelope calculations illustrate what’s at stake. Taiwan produces 11 percent of the world’s memory chips. More important, it fabricates 37 percent of the world’s logic chips. Computers, phones, data centers, and most other electronic devices simply can’t work without them, so if Taiwan’s fabs were knocked offline, we’d produce 37 percent less computing power during the following year

硅谷大多数知识在战争或者地震的情况下都能轻易地被转移，这已经被 pandemic 期间大多数员工居家办公所验证了。大科技公司的利润甚至上升了。如果 Facebook 的华丽总部沉入 San Andreas 断层，该公司大气都不用喘。如果 TSMC 的工厂沉入了车笼埔断层（上一次造成了 1999 年的 921 大地震），世界经济都会为之震动。一点爆炸（无论是意外还是蓄意）都能造成可观的损失。一些小学计算：台湾生产世界上 11% 的记忆芯片。更重要的是，它生产世界 37% 的逻辑芯片。电脑、手机、数据中心、绝大多数电子设备没有它们就是废铁。所以如果台湾的工厂停工，接下来一年全球将失去 37% 的计算力。

> The most advanced lithography machines, which are used to pattern millions of microscopic transistors, each far smaller than a human cell, are made by ASML in the Netherlands. Each machine costs well over $100 million dollars and is built from hundreds of thousands of components. (ASML) Today, advanced chips possess tiny, three-dimensional transistors, each smaller than a coronavirus, measuring a handful of nanometers (billionths of a meter) wide

(图片脚注)世界上最先进的光刻机，用来印刻上百万晶体图样，每个比人类细胞还小。它们由荷兰 ASML 制造。每台机器造价超过 1 亿美元，由成百上千元件构成。如今，先进芯片由微小的、三维的晶体构成，每个比新冠病毒还小，只有几纳米大。
