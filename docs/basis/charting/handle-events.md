# 处理事件

在本页，您将会学习如何放置以及编辑判定线事件。

将鼠标移动至编辑窗口右半侧，这里是编辑事件的区域。

如同放置 Hold 音符一样在事件的开始位置按下 R 键，移动鼠标到结束位置，再次按下 R 键，即放置了一个事件。与 Hold 音符同样，`ESC`
键可以终止这一过程。

稍微不同的是，***同层同类事件*** 原则上不允许重叠，若移动鼠标时事件重叠，则其会变为红色且无法放置。

![事件重叠](/assets/imgs/contents/事件重叠.avif)

事件编辑窗口有五栏，从左到右对应着五种普通事件：MoveX，MoveY，Rotate，Alpha，Speed（关于事件对应的效果，请参阅 [事件](../inside-chart/event.md)
）。

![五种事件](/assets/imgs/contents/五种事件.avif)

如果谱面开启了 XY 绑定，那么对 MoveX/Y 的放置、时间编辑、删除、切割等**均会同时作用在一个与它时间相等（开始时间与结束时间均相同）的
MoveY/X 上，这是为了方便保持谱面的 *等时性质***。

放置一个事件后，该事件的**头部和缓动类型会自动继承时间上的上一个该类事件的尾部和缓动类型**
，且尾部与头部相同。软件会帮你自动选择新放置的事件，进入事件编辑。

![编辑事件](/assets/imgs/contents/编辑事件.avif)

这些文本框的含义与前文一致，缓动类型右侧偏白的下拉列表可以点击显示选项，数字文本框与两个下拉列表的组合是关联的，该缓动类型所对应的曲线会在下方实时展示。一般来说，编号更大的曲线会更加陡峭。

点击删除或按下 Delete 或按下 D 键和鼠标右键来删除事件，点击取消可以还原掉未保存的编辑，点击保存或按 Enter
键可以保存编辑，点击箭头或 `ESC` 键可以退出编辑。

::: warning
速度事件缓动类型只能为 1（linear），不可编辑（实际上可以编辑，但不会起任何效果）。
:::

为了方便编辑，选中事件后，按下 A 键，S 键，以及按住 `CTRL` 键并使用鼠标滚轮都可能有快捷效果。

- 对于 MoveX/Y，Rotate，Speed 事件，按下 A 键会使头尾部值变为原来的相反数。
- 对于 Alpha 事件，按下 A 键会使尾部变为 $0$，按下 S 键会使尾部变为 $255$。
- 对于所有事件，按住 `CTRL` 键并使用鼠标滚轮，可以使事件的尾部数据发生微调（以默认设置参数为例，一次滚动会使 MoveX/Y，Alpha
  尾部 $±10$，使 Rotate 尾部 $±0.25$，使 Speed 尾部 $±0.1$）。

对任意勾定事件，在编辑时，对头 / 尾部数据的更改会即刻反应到尾 / 头部上。

**快捷编辑**：

- ***粘合***：点击后将上一个该种类事件的尾部填入其头部。
- ***切割***：选择事件并点击切割后，如果全局时间最近的横线不在该事件控制的时间范围内，则会自动选定事件头部时间开始切割，否则会以全局时间最近的横线为中心沿时间前后切割事件，切割的间距为
  $\frac{横线距离}{切割密度}$（可在设置中调整，请参阅 [设置界面](../others/settings.md)）。如果开启了 XY 绑定，则切割 MoveX/Y
  事件会导致相同时间的 MoveY/X 事件的切割。

![切割](/assets/imgs/contents/切割.avif)

- ***随机***：在尾部随机填入数值。
- ***递推***：根据上两个事件推出这个事件的头部和尾部，比如上两个事件是 $0 => 50$，$50 => 100$，递推得到的就是 $100 => 150$。
- ***拆分***：可以从当前时间将选中的事件切成两个，两个事件变化程度按时间分配，缓动类型与原事件相同。

比如 $1$~$4$ 拍的 $0 => 150$ 的事件，缓动为 4，从 $2$ 拍切开变成 $1$~$2$ 拍，$0 => 50$，缓动为 4 和 $2$~$4$ 拍，$50 =>
150$，缓动为 4 的两个事件。

时间可以用小数转义，比如横线数为 4，填入 12.1 表示 $12\frac{1}{4}$，12.2 表示 $12\frac{2}{4} = 12\frac{1}{2}$。

缓动可以设置左右端点，该事件将以左右端点框出的曲线段作为实际的缓动曲线，如下图：

![缓动设置左右端点](/assets/imgs/contents/缓动设置左右端点.avif)

## 事件取样

双击一个事件后，可以通过点击屏幕来快捷编辑事件。鼠标左键点击是修改事件结束数值，右键是修改起始数值。

::: tip
旋转事件需要点两次来确定角度。

MoveX 和 MoveY 事件会被同时修改。
:::

可以配合 [视野](../UI/tools-bar.md) 使用。

![事件取样](/assets/imgs/contents/事件取样.avif)

## 预制事件

点击 ***预制事件***，进入到预制主界面：

![预制事件](/assets/imgs/contents/预制事件.avif)

单击右下角的创建按钮（一个文件夹图标里面有一个向下的箭头），框选你想要预制的事件（两次框选以移出），点击叉号以中止预制流程。

再次单击加号进入到保存界面，输入信息后点击右下角按钮即可保存。

![创建预制事件](/assets/imgs/contents/创建预制事件.avif)

保存文件位于 `[RPE 目录]/Prefab/` 下，文件名为 `[标识名].json`。预制文件可以随意增删，程序会自动配置。

在预制主界面点击想要应用的预制件右侧的双箭头，会进入到应用界面：

![应用预制事件](/assets/imgs/contents/应用预制事件.avif)

文本框表示的是该条线上的事件将会复制到哪一条线上，默认为原线号。

值为 -1 表示不复制这条线的事件，点击右上角的按钮可以将全部文本框内容置为 -1。

正下方的文本框代表预制起点会对应到哪一个时刻，可转义，点击对勾进行复制，此操作可撤销。

## 魔法棒

默认开启，可点击魔法棒按钮关闭。

开启后，点击事件会出现四个滑条，从左到右分别控制数值范围、起点数值、终点数值以及缓动类型。

![魔法棒](/assets/imgs/contents/魔法棒.avif)
