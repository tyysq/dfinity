# Rust语言

**如何使用Rust语言工作的介绍**

Rust语言是一种强大，安全可靠的现代变成语言，拥有活跃的开发者社区。由于Rust可以编译为WebAssembly，因此它提供了丰富的开发环境来编写可在互联网计算机上运行的应用程序。为了帮助铺平可以在Internet计算机上部署的用Rust编写应用程序的方式，DFINITY提供了一些工具来简化该过程。

这些工具就是用于支持Rust的DFINITY Canister开发套件（CDK），包括以下主要库：

<table>
  <thead>
    <tr>
      <th style="text-align:left">Package&#x5305;</th>
      <th style="text-align:left">Description&#x63CF;&#x8FF0;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">ic-types</td>
      <td style="text-align:left">ic-types&#x5E93; &#x5B9A;&#x4E49;&#x4E86;&#x7528;&#x4E8E;&#x4E0E;&#x4E92;&#x8054;&#x7F51;&#x8BA1;&#x7B97;&#x673A;&#x526F;&#x672C;&#x8FDB;&#x884C;&#x901A;&#x4FE1;&#x7684;&#x7C7B;&#x578B;&#xFF0C;&#x4EE5;&#x53CA;&#x5728;&#x6784;&#x5EFA;&#x8981;&#x4F5C;&#x4E3A;&#x4E92;&#x8054;&#x7F51;&#x8BA1;&#x7B97;&#x673A;&#x4E0A;&#x7684;Canister&#x7684;&#x5E94;&#x7528;&#x7A0B;&#x5E8F;&#x65F6;&#x4F7F;&#x7528;&#x7684;&#x7C7B;&#x578B;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ic-agent</td>
      <td style="text-align:left">ic-agent &#x5E93;&#x5141;&#x8BB8;&#x4E0E;Internet&#x8BA1;&#x7B97;&#x673A;&#x526F;&#x672C;&#x76F4;&#x63A5;&#x901A;&#x4FE1;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ic-utils</td>
      <td style="text-align:left">
        <p>The ic-utils library provides utilities for managing calls and applications
          deployed as canisters.</p>
        <p>ic-utils&#x5E93;&#x63D0;&#x4F9B;&#x7A0B;&#x5E8F;&#xFF0C;&#x7528;&#x4E8E;&#x7BA1;&#x7406;Canister&#x5E94;&#x7528;&#x7A0B;&#x5E8F;&#x548C;Canister&#x4E4B;&#x95F4;&#x7684;&#x8C03;&#x7528;&#x3002;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ic-cdk</td>
      <td style="text-align:left">ic-cdk&#x63D0;&#x4F9B;&#x4E86;&#x4F7F;Rust&#x7A0B;&#x5E8F;&#x80FD;&#x591F;&#x4E0E;&#x4E92;&#x8054;&#x7F51;&#x8BA1;&#x7B97;&#x673A;&#x7684;&#x4E3B;&#x7CFB;&#x7EDF;API&#x4EA4;&#x4E92;&#x7684;&#x6838;&#x5FC3;&#x65B9;&#x6CD5;&#x3002;
        &#x8BE5;&#x5E93;&#x5145;&#x5F53;Rust CDK&#x7684;Runtime&#x6838;&#x5FC3;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ic-cdk-macros</td>
      <td style="text-align:left">ic-cdk-macros&#x5E93;&#x5B9A;&#x4E49;&#x4E86;&#x6709;&#x52A9;&#x4E8E;&#x6784;&#x5EFA;&#x64CD;&#x4F5C;&#x7AEF;&#x70B9;&#x548C;API&#x7684;&#x8FC7;&#x7A0B;&#x5B8F;&#x3002;
        &#x8BE5;&#x5E93;&#x5305;&#x542B;&#x7528;&#x4E8E;&#x66F4;&#x65B0;&#xFF08;update&#xFF09;&#xFF0C;&#x67E5;&#x8BE2;&#xFF08;query&#xFF09;&#xFF0C;&#x5BFC;&#x5165;&#xFF08;import
        &#xFF09;&#x548C;&#x5176;&#x4ED6;&#x91CD;&#x8981;&#x64CD;&#x4F5C;&#x7684;&#x5173;&#x952E;&#x5B8F;&#x3002;</td>
    </tr>
    <tr>
      <td style="text-align:left">ic-cdk-optimizer</td>
      <td style="text-align:left">ic-cdk-optimizer&#x662F;&#x7528;&#x4E8E;&#x51CF;&#x5C11;WebAssembly&#x6A21;&#x5757;&#x5927;&#x5C0F;&#x7684;&#x5E2E;&#x52A9;&#x7A0B;&#x5E8F;&#x5E93;&#x3002;</td>
    </tr>
  </tbody>
</table>

![](https://uploader.shimo.im/f/FX9xtDHEueSiKyi8.png!thumbnail)

