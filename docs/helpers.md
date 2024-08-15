- 文档结构
<pre>
└── docs（英文根目录）
    ├── README.md(index页面)
    ├── _navbar.md(顶部导航栏)
    ├── _sidebar.md(左侧导航栏)
    └── zh-cn（中文）
        ├── README.md(index页面)
        └── _navbar.md(顶部导航栏)
        └── _sidebar.md(左侧导航栏)
    └── jp（日语）
        ├── README.md(index页面)
        └── _navbar.md(顶部导航栏)
        └── _sidebar.md(左侧导航栏)   
    └── _media(存放视频等多媒体资料)
        ├── en(存放英文特定media资料用)
        ├── zh-cn(存放中文特定media资料用)
        ├── jp(存放日语特定media资料用)
    └── _images(存放图片)
        ├── en(存放英文特定资料用)
        ├── zh-cn(存放中文特定资料用)
        ├── jp(存放日语特定资料用)
    └── inc(存放共通页面，方便别的页面引用的md文件)
</pre>
- 命名规则
<pre>
└──组件介绍:的MD文件名，统一用 c-xx(组件类型)命名，参考zh-cn里的命名
└──进阶使用:的MD文件名，统一用 ad-xx(内容简写)命名，参考zh-cn里的命名
└──应用场景:的MD文件名，统一用 sc-xx(场景见简写)命名，参考zh-cn里的命名
└──支持:的MD文件名，统一用 sp-xx(类型)命名，参考zh-cn里的命名
    └── _images(存放图片的名字，根据他使用在对应的md文件的名字-XXX番号命名)（参考zh-cn）
</pre>