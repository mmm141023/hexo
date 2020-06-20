---
title: CSS之数据样式
date: 2020-05-16 21:33:54
tags: 
    - CSS
categories: 
    - 前端
    - 后盾人
---
## 表格

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

表格可以非常快速的部署数据，灵活控制表格样式是必要的。表格不能设置外边距。

### 定制表格

除了使用 `table` 标签绘制表格外，也可以使用样式绘制。

| 样式规则           | 说明         |
| ------------------ | ------------ |
| table              | 对应 table   |
| table-caption      | 对应 caption |
| table-row          | 对表 tr      |
| table-row-group    | 对应 tbody   |
| table-header-group | 对应 thead   |
| table-footer-group | 对应 tfoot   |

![image-20190819143313891](http://houdunren.gitee.io/note/assets/img/image-20190819143313891.eb8094c1.png)

```text
<style>
	.table {
    display: table;
    border: solid 1px #ddd;
  }

  .table nav {
    display: table-caption;
    text-align: center;
    background: black;
    color: white;
    padding: 10px;
  }

  .table section:nth-of-type(1) {
    font-weight: bold;
    display: table-header-group;
    background: #555;
    color: white;
  }

  .table section:nth-of-type(2) {
    display: table-row-group;
  }

  .table section:nth-of-type(3) {
    display: table-footer-group;
    background: #f3f3f3;
  }

  .table section ul {
    display: table-row;
  }

  .table section ul li {
    padding: 10px;
    display: table-cell;
    border: solid 1px #ddd;
  }
</style>

<article class="table">
        <nav>后盾人在线教程</nav>
        <section>
            <ul>
                <li>标题</li>
                <li>说明</li>
            </ul>
        </section>
        <section>
            <ul>
                <li>后盾人</li>
                <li>houdunren.com</li>
            </ul>
            <ul>
                <li>开源系统</li>
                <li>hdcms.com</li>
            </ul>
        </section>
        <section>
            <ul>
                <li>不断更新视频</li>
                <li>努力加油</li>
            </ul>
        </section>
</article>
```

### 表格标题

通过 `caption-side` 可以设置标题位置，值可以设置为 `top | bootom`。

![image-20190819133516640](http://houdunren.gitee.io/note/assets/img/image-20190819133516640.a7ca8fa9.png)

```text
<style>
  table caption {
    background: black;
    color: white;
    padding: 10px;
    caption-side: top;
  }
</style>

<table border="1">
        <caption>后盾人线上视频课程</caption>
        <tr>
            <td>houdunren.com</td>
            <td>后盾人</td>
        </tr>
</table>
```

### 内容对齐

水平对齐使用 `text-align` 文本对齐规则

```text
<style>
	table tr td {
    height: 100px;
    text-align: center;
  }
</style>
```

垂直对齐使用 `vertical-align` 处理

| 属性   | 说明     |
| ------ | -------- |
| top    | 顶对齐   |
| middle | 垂直居中 |
| bottom | 底部对齐 |

```text
<style>
	table tr td {
    height: 100px;
    vertical-align: bottom;
    text-align: center;
  }
</style>
```

### 颜色设置

为表格设置颜色与普通标签相似，可以为 `table | thead | tbody | caption | tfoot| tr| td` 设置颜色样式。

![image-20190819145908071](http://houdunren.gitee.io/note/assets/img/image-20190819145908071.d26a4066.png)

```text
<style>
	table tr {
    color: white;
  }
  table tr:nth-child(odd) {
    background: red;
  }
  table tr td:nth-child(even) {
    background: #067db4;
  }
</style>
```

使用选择器设置表格隔行变色

![image-20190820130542137](http://houdunren.gitee.io/note/assets/img/image-20190820130542137.16023728.png)

```text
<style>
        table thead tr {
            background: #118d68;
            color: #fff;
        }

        table tbody tr:nth-child(odd) {
            background: #1bb385;
            color: white;
        }
</style>
```

### 边框间距

设置单元格间距，设置间距上下10px ，左右 50px。

```text
table {
    border-spacing: 50px 10px;
}
```

### 边框合并

默认表格边框间是有间距的，以下示例将边框合并形成细线表格。

![image-20190819141518119](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAWoAAABOCAYAAAAJklx3AAAMSWlDQ1BJQ0MgUHJvZmlsZQAASImVVwdYU8kWnltSSWiBCEgJvYlSpEsJoUUQkCrYCEkgocSQEETsLssquHYRARu6KqLoWgBZK+paF8HuWh6KqCjrYsGGypsUWNf93nvfO9839/45c85/SubeOwOATg1PKs1FdQHIkxTI4iNCWJNS01ikLkAAIwEV6AJ7Hl8uZcfFRQMoQ/e/y9sbAFHer7oouf45/19FTyCU8wFA4iDOEMj5eRAfBAAv4UtlBQAQfaDeemaBVImnQGwggwlCLFXiLDUuUeIMNa5U2STGcyDeDQCZxuPJsgDQboZ6ViE/C/Jo34LYVSIQSwDQIUMcyBfxBBBHQjwqL2+GEkM74JDxFU/W3zgzhjl5vKxhrK5FJeRQsVyay5v1f7bjf0termIohh0cNJEsMl5ZM+zbrZwZUUpMg7hXkhETC7E+xO/FApU9xChVpIhMUtujpnw5B/YMMCF2FfBCoyA2hThckhsTrdFnZIrDuRDDFYIWiQu4iRrfxUJ5WIKGs0Y2Iz52CGfKOGyNbwNPpoqrtD+tyElia/hviYTcIf43xaLEFHXOGLVQnBwDsTbETHlOQpTaBrMpFnFihmxkinhl/jYQ+wklESFqfmxapiw8XmMvy5MP1YstFom5MRpcVSBKjNTw7ObzVPkbQdwslLCThniE8knRQ7UIhKFh6tqxdqEkSVMv1iktCInX+L6S5sZp7HGqMDdCqbeC2FRemKDxxQML4IJU8+Mx0oK4RHWeeEY2b3ycOh+8CEQDDggFLKCAIwPMANlA3Nbb1At/qWfCAQ/IQBYQAheNZsgjRTUjgdcEUAz+gEgI5MN+IapZISiE+s/DWvXVBWSqZgtVHjngMcR5IArkwt8KlZdkOFoyeAQ14n9E58Ncc+FQzv1Tx4aaaI1GMcTL0hmyJIYRQ4mRxHCiI26CB+L+eDS8BsPhjvvgvkPZ/mVPeEzoIDwkXCd0Em5PFy+SfVMPC0wAnTBCuKbmjK9rxu0gqyceggdAfsiNM3ET4IKPhZHYeBCM7Qm1HE3myuq/5f5bDV91XWNHcaWglBGUYIrDt57aTtqewyzKnn7dIXWuGcN95QzPfBuf81WnBfAe9a0lthg7gJ3FTmLnsSNYE2Bhx7Fm7BJ2VImHV9Ej1SoaihavyicH8oj/EY+nianspNy13rXH9ZN6rkBYpHw/As4M6SyZOEtUwGLDN7+QxZXwR49iubu6+QKg/I6oX1OvmarvA8K88Jcu/wQAvmVQmfWXjmcNwOHHADDe/qWzfgUfjxUAHG3nK2SFah2uvBDg10kHPlHGwBxYAwdYjzvwAv4gGISB8SAWJIJUMA12WQTXswzMBHPAQlAKysEKsBZUgU1gK9gJ9oD9oAkcASfBr+AiaAfXwR24errBc9AH3oIBBEFICB1hIMaIBWKLOCPuiA8SiIQh0Ug8koqkI1mIBFEgc5DvkHJkFVKFbEHqkJ+Rw8hJ5DzSgdxGHiA9yCvkI4qhNNQANUPt0DGoD8pGo9BEdCqaheajxWgJugytRGvR3WgjehK9iF5HO9HnaD8GMC2MiVliLpgPxsFisTQsE5Nh87AyrAKrxRqwFvg/X8U6sV7sA07EGTgLd4ErOBJPwvl4Pj4PX4pX4TvxRvw0fhV/gPfhXwh0ginBmeBH4BImEbIIMwmlhArCdsIhwhn4NHUT3hKJRCbRnugNn8ZUYjZxNnEpcQNxL/EEsYPYRewnkUjGJGdSACmWxCMVkEpJ60m7ScdJV0jdpPdkLbIF2Z0cTk4jS8iLyBXkXeRj5CvkJ+QBii7FluJHiaUIKLMoyynbKC2Uy5RuygBVj2pPDaAmUrOpC6mV1AbqGepd6mstLS0rLV+tiVpirQValVr7tM5pPdD6QNOnOdE4tCk0BW0ZbQftBO027TWdTrejB9PT6AX0ZfQ6+in6ffp7bYb2aG2utkB7vna1dqP2Fe0XOhQdWx22zjSdYp0KnQM6l3V6dSm6drocXZ7uPN1q3cO6N3X79Rh6bnqxenl6S/V26Z3Xe6pP0rfTD9MX6Jfob9U/pd/FwBjWDA6Dz/iOsY1xhtFtQDSwN+AaZBuUG+wxaDPoM9Q3HGuYbFhkWG141LCTiTHtmFxmLnM5cz/zBvPjCLMR7BHCEUtGNIy4MuKd0UijYCOhUZnRXqPrRh+NWcZhxjnGK42bjO+Z4CZOJhNNZppsNDlj0jvSYKT/SP7IspH7R/5uipo6mcabzjbdanrJtN/M3CzCTGq23uyUWa850zzYPNt8jfkx8x4LhkWghdhijcVxi2csQxablcuqZJ1m9VmaWkZaKiy3WLZZDljZWyVZLbLaa3XPmmrtY51pvca61brPxsJmgs0cm3qb320ptj62Itt1tmdt39nZ26XY/WDXZPfU3siea19sX29/14HuEOSQ71DrcM2R6OjjmOO4wbHdCXXydBI5VTtddkadvZzFzhucO0YRRvmOkoyqHXXThebCdil0qXd5MJo5Onr0otFNo1+MsRmTNmblmLNjvrh6uua6bnO946bvNt5tkVuL2yt3J3e+e7X7NQ+6R7jHfI9mj5djnccKx24ce8uT4TnB8wfPVs/PXt5eMq8Grx5vG+907xrvmz4GPnE+S33O+RJ8Q3zn+x7x/eDn5Vfgt9/vT38X/xz/Xf5Px9mPE47bNq4rwCqAF7AloDOQFZgeuDmwM8gyiBdUG/Qw2DpYELw9+AnbkZ3N3s1+EeIaIgs5FPKO48eZyzkRioVGhJaFtoXphyWFVYXdD7cKzwqvD++L8IyYHXEikhAZFbky8ibXjMvn1nH7xnuPnzv+dBQtKiGqKuphtFO0LLplAjph/ITVE+7G2MZIYppiQSw3dnXsvTj7uPy4XyYSJ8ZNrJ74ON4tfk782QRGwvSEXQlvE0MSlyfeSXJIUiS1JuskT0muS36XEpqyKqVz0phJcyddTDVJFac2p5HSktO2p/VPDpu8dnL3FM8ppVNuTLWfWjT1/DSTabnTjk7Xmc6bfiCdkJ6Sviv9Ey+WV8vrz+Bm1GT08Tn8dfzngmDBGkGPMEC4SvgkMyBzVebTrICs1Vk9oiBRhahXzBFXiV9mR2Zvyn6XE5uzI2cwNyV3bx45Lz3vsERfkiM5PcN8RtGMDqmztFTame+Xvza/TxYl2y5H5FPlzQUGcMN+SeGg+F7xoDCwsLrw/czkmQeK9IokRZdmOc1aMutJcXjxT7Px2fzZrXMs5yyc82Aue+6Weci8jHmt863nl8zvXhCxYOdC6sKchb8tcl20atGb71K+aykxK1lQ0vV9xPf1pdqlstKbP/j/sGkxvli8uG2Jx5L1S76UCcoulLuWV5R/WspfeuFHtx8rfxxclrmsbbnX8o0riCskK26sDFq5c5XequJVXasnrG5cw1pTtubN2ulrz1eMrdi0jrpOsa6zMrqyeb3N+hXrP1WJqq5Xh1TvrTGtWVLzboNgw5WNwRsbNpltKt/0cbN4860tEVsaa+1qK7YStxZufbwtedvZn3x+qttusr18++cdkh2dO+N3nq7zrqvbZbpreT1ar6jv2T1ld/ue0D3NDS4NW/Yy95bvA/sU+579nP7zjf1R+1sP+BxoOGh7sOYQ41BZI9I4q7GvSdTU2Zza3HF4/OHWFv+WQ7+M/mXHEcsj1UcNjy4/Rj1WcmzwePHx/hPSE70ns052tU5vvXNq0qlrpyeebjsTdebcr+G/njrLPnv8XMC5I+f9zh++4HOh6aLXxcZLnpcO/eb526E2r7bGy96Xm9t921s6xnUcuxJ05eTV0Ku/XuNeu3g95nrHjaQbt25Oudl5S3Dr6e3c2y9/L/x94M6Cu4S7Zfd071XcN71f+y/Hf+3t9Oo8+iD0waWHCQ/vdPG7nj+SP/rUXfKY/rjiicWTuqfuT4/0hPe0P5v8rPu59PlAb+kfen/UvHB4cfDP4D8v9U3q634pezn4aulr49c73ox909of13//bd7bgXdl743f7/zg8+Hsx5SPTwZmfiJ9qvzs+LnlS9SXu4N5g4NSnoyn2gpgcKCZmQC82gEAPRXuHdoBoE5Wn/NUgqjPpioE/hNWnwVV4gXAjmAAkhYAEA33KBvhsIWYBu/KrXpiMEA9PIaHRuSZHu5qLho88RDeDw6+NgOA1ALAZ9ng4MCGwcHP22CytwE4ka8+XyqFCM8Gm8coUXv3C/Ct/BuksX9wSo4AMwAAAAlwSFlzAAAWJQAAFiUBSVIk8AAAGPRJREFUeAHtnQO0PLnThrO2bdu2bdv27m9t23vWtm3bOGvbtr3z1ZNvK/9MT2N6pmfunLtV59zbSirJm+5KpSqVGagm5IwMAUPAEDAEehaBgXu2ZlYxQ8AQMAQMAY+ACWp7EQwBQ8AQ6HEETFD3eAdZ9QwBQ8AQMEFt74AhYAgYAj2OgAnqHu8gq54hYAgYAiao7R0wBAwBQ6DHETBB3eMdZNUzBAwBQ8AEtb0DhoAhYAj0OAImqHu8g6x6hoAhYAgMmgXBdNNNl/XI7hsChoAhYAiUQODFF18skboxqWnUjZjYHUPAEDAEegqBTI1aa9nuSKB87GgIGAKdQ+DAAw/0zPfff//OFWKcSyNQlWXCNOrS0FsGQ8AQMAS6i4AJ6u7ibaUZAoaAIVAaARPUpSGzDIaAIWAIdBcBE9TdxdtKMwQMAUOgNAImqEtDZhkMAUPAEOguAiaou4u3lWYIGAKGQGkETFCXhswyGAKGgCHQXQRMUHcXbyvNEDAEDIHSCBQGvJTmaBkMAUPgP4PAZ5995gYeeGA3+uijd73N/C73l19+6T7++GM34YQTupFGGqntOrz++uvunnvu8XxWXHFFN/bYY7fNswoGJqirQNF4GAL9GIGff/7Zvf322+6tt95yb7zxhkOYvfzyy+6pp57yrZ555pn9OQK7Svr999+9EEYQf/DBB+7DDz/0x/fee8/Xh7oobbbZZu7MM8/Uy5aPzz77rNtmm218/gkmmMAEdctIWkZDwBBoCYG//vrL/fjjjw7By5G/n376KZzrPY7fffede/PNNx2C64svvsgt75lnnnFXXHGFW2uttTLTffTRR+6aa67xZVP+L7/8Euqi9eH4/fff+7J//fVX/zyTYeLBWWed5QYMGOCmnnrqxJNyl3///XfIMMggg4Tzvj4ppVHTYbvssouv8wwzzOB23nnnvq5/n5V/2223ucsuu8yXz2g+33zz9VldrGBDoAgBtOHJJpusKFnTz8cdd1zHPhYIximnnNLNOOOMuXnRwhGk7dJwww3nJppoIjfJJJP44/jjj+/4G2+88bz5o13+//zzT2Ax6KClxGPI14mTUjXBHnXRRRf5ejDi/pcF9WuvvRawmGOOOUxQd+LtNJ59ggDCcLTRRnNjjTWWG3XUUf0fNuApppjCTT755F5IDjvssC3XDSE/8sgjuyGGGMJRlv7Bk3OOwwwzjHv11VfdOeec48s59NBDvUlihBFGaLncZjIy61AabLDB9LTPj6UEdZ/X1ipgCBgCbSOw2mqrueWWW84NOeSQbuihh/ZOuFFGGcUfcch1WkCdfvrpbplllilsx5133hkE9UwzzeQ6LaSp0B9//BHqNdRQQ4Xzvj4xQd3XPWDlGwJdRmDOOed06623XpdLLV/ct99+GzKhgXeD3n333VAMWn2vkAnqXukJq4ch8B9BYL/99nOnnXZaYWtjobn55pt7O3RRpkUXXbQtWzgmTSVMM71CJqh7pSesHobAfwQBVomUpRdeeMHxV0RjjDFGUZLc5/EPpTz99NNu0kknzU3frYeVCWqci08++aTDU4rDYZxxxnEDDTRQqXZ89dVX7qWXXnJ4XvHq4s0ty6NUgQWJWULEy/H55587HCB4uHvBbkW9WDbFEiY84Kz3LOuh/vrrr/1aWJZijTjiiA4bIPbKNMLBgteedax8CFNNNZW3b6alLboHr+eff95RPsEE9HMnMKWurHT4888/PT6sCshqX1adqStrdVlahu12mmmmKc1DecPrueee80vOpp12Wu+s02fJ4yeffOIQEgSRsKKiatvsgw8+6B15yXKruJ511lkdzvU8Qj4UrRIh//333x+WBq6++up5LMOzxRZbLJyXPfntt9/cO++8E7LdeOONbo011gjXfXoi0T2pJC9Tjb+Y5AOrSWX9nzgj/KNLL720Nttss4X7+lxestoNN9wQZ089l3WctW233bZGes2rR/EA1yhHwEvNy83tttvO5yW/fAiZ6Xhw7733hrS77757ZtrLL7+8Nv3006fW55hjjqnJWsvacccdF56ffPLJdbzIS31EuNfdT7sQb3ao0/XXX1+XZOKJJ67jc9ddd9UWXHDBUK7ixBE+4gipy8+FBCYE/rKMsCaCq7bnnns28FhllVUa8srAW5Nlhw1pKY82nnTSSQ159MYmm2wSyqVf6EPKoE/jenO+7rrr1iTCTLO2fBQBV5MPOrUMytlggw1qMrUt5H/33XenvtPwECFTo79FmUjlE+MtduCaDKY1sEi2Gz70gwgHz4e+O/jggz3/JD4rrbRSjbbl0QEHHFDjL4tkTXQD7slyqrimDWkEpsr/5ptvTkvScI9vnzxg1Q2i77SOepSgm7aKTpOjrTB0WZnSCkgKalmq19AwbaAe5bfcsoqoyTQj9cXUvHrkJb/22mtT+YgHO9RBIqVS0+hNWfsc0m611VZ6OxwRwNRXy806IlgQ2Po8KajjjzIwzziJhSYDREwxn+uuuy6Up+Umj+Ik8oI45hH3GVjF5cX5k4L67LPPLiyP/GAhgQpxkf487pcLLrjAC+24vOQ5bRWbZAOfZm888sgjhWVomaIppbJlEEPYabq84worrFD75ptvGvjEeDPILbHEErn8eC4zpNrCCy+cmw58ZIbQUJ7e6I+CWmawHpOlllpKm9nRI4pSss8ZYNqhNDnaCr+WTR833XST4w8S7dTJi+anU0zJcRYwpYb4sc211167wdbDVDr+4UfRQJ0ITyfauZ9eMvVjzTamB3itvPLK/loEg+fbiX977723O+KIIwJr+RgdfwQKUAf2ADj22GPdxRdf7GS2ENJ140S0Kl8M9VlnnXW8CYJpmmi1Tm1+jz/+uLvwwgvdxhtvnFqlq666qu6+aOd+Ck5fYGZSguf222+vl34pFVFn4MDeCvSN/ogqWOD0eeihhzLNVKLJel6YjnbddVdv7mB6L4Ovu/LKK/0z8OW9of5lSYS0m3feeUM2ptZbbLGFm2WWWfxSM8xpRx55ZJjWLr/88g5bpHxEIQ8nW2+9tSPCTQmsl156aZ+OEGbKkUHZP6b/WT3B+5nldAITSISsE03TESSGee/88893t9xyi392xx13eP465d53333d/PPP7002TzzxhNMfrQWfHXfc0TEdb4VEOIRsMli7TTfdNFxXeVJmvw1RTNwZZ5yRWfwrr7zinz388MNuoYUWykzHA5ltljb/JRk+8MADyVu+nxZZZJGG+12/kSXd00aCWFuQivrRh+l4kiQ2v067SdNedVoDH0ZOid9PsvGamgj5MMphTvjhhx/q0sWaWzsatXyIoRzqdPjhh6dOb5m2adv12A2NmrIwtySJKTNardYFjGJK6zNMVRK8FCcL59xXXhzFOx+exSf0F1NSTXvrrbfGj2txv5AGkwRmgCSdeuqpgQfpmKKXIUwQzCS0HmioaZouOMXaLfWJiXdHeXA8+uij48fhHPNZPNNJ9kkSb8xfsk9GyM8JdZZVDHXlUSa8k/TYY4/VpZNBJ5nEXxdp1HH7svo0lXFFN9NMH2AcY97OeZrZr0zVZSlgXV3UnEv/MdNuldLkaCu8WjZ9ACrT6Cw677zzQsPnmWeeumQI97hTxFlX9zy+4KWO7bL77LNP/LhOILQjqLfccstQpw033LCujOSFaGchLe3ohqBm+pdlF2VgjPEUR12oclJwYPfGL5BFDKrKi0Eyj8QpFdIm+zgW1AweacIT3nwEsqlP4JNllsiqB34QrS8CVDTPrKQ12QIhpCWP2ofBlfornz322COTBw8QqJqWMuP3N4m3zGJSeSX7DMGdRZiltLwsfkWCWjT3wENmMVlFdex+kaDG1ySRzqX+4gG6XUEd+5wYxGVfkoCXbBXRMi49IaizPj5aFWtmvMwx4VzRFy/Pqad5YsGe1BhjgdCOoI61JJnOatGpR9k4pk6r6oag5kPLo1jQiCkkJE0KDmzdWYTQ1H7hmNQE0/LF5caOurhf9tprr7Ss4V5sFz7xxBPD/WZO4hkXDtUiwjGnbcSuDeHo1HscY8GbxS9ut5hrQrIYb96prMGVDLzLWq6YEQOP5ImY40K6rDYWCWqEjZbVrt01Wb9mruOBQmdfsUadN8Bm8cdxqW1qR1CTN+4LfFnxPbTqtNlgVr3i+1UJ6pZt1FL53P1fpeGC4f8T9jWWJ+kSMrZIVMLeWkQsYocfm0Lxx45f7ew1kCwPuyF1hGhXbDtPpuV6+OGHd6LhBvtqWpqq77GVZB5hP8aGCmH/ZbldGmF3zSK2k1QCb9G+9TLziG1Yy8XOyn4QSZp99tmTt+quWV6oxFK4MhQHKLB/cBFhF08Su8QpyQDT1N7KG220UWh3vN2m8uEoK2My7fY8p894nyH20sgi3kkl3v1WKCvKT7RH/z21wlPz8C2qr0HvJY/4NpT4fpLEPkJp95Pp4muWBFdB4kQM/cB3JiYy329sd4ovhncSW/oOO+xQRXEt8WhZULOmNI9Y/6zClXQyyvjkHGNBnfeCxvwRAPpSszcujpmqSOytgVUsNMLNlBPW/3aT2Bwnj2InjmjGqUlx1OatS2fdsRJYNxM8oH1CPnWIKQ89sqY+j+K6M6CXIXWkkoe10q1QLKibDXCIB7H4fY7LLwp7jvfUYN+NLBp88MGzHjV9n8FbKcb79ttvD0qKPu/EMRbU7CuSJAatviLR7EPRCGb9RsQEGpzmOHnXX3/9XOU0MOnAScuCutWXh1FQtVfaI9PDppoVf4SMcFUKakZzpTHHHFNPc4+xlpObsIceFg2KsUZNtWMh3EwzGEC7SbGWSLnNvkvJOrKiQ6nZX/SI35P3339fs/fskdVYSuyKl0asyilDBBXF33JeXoLGlNIEtT7r9pEfGxCTqS+W9i+77LKhCqyEYkUbK4ZoJ8d4VVhI2IWTlgV1q3VLRlkRZddMxFisEcQfSav1iPPFmmOzwglzSX+jGFeEHi9mGSIqrZuUnCoTWZanmWbVLRZczfZ/rCEWzRiyyu3mfRVGmGPSlhPKKqzSS/8wW0rAW1PNiGdbsUavmVESypoz0YQPOeQQZVH6yPJJlnEqSWyE/1kxveaIJn3JJZd48wffA+Y1lmV2m7ouqPm5HuxAOmVFmyFMtoh0TSXpsswOhFTnUaw5x+liTfPdaPesOE3yvNl0hDDHU9wkn3gASj7r9nWMK/sRs669l4lf4GDNtNqIwTI2SaTVnXXPauJhbS5CI7arNzsriAVPWU00rV6dvIdSoQMQ5q++IMLBIfpLfVX+xr//GHTLCuq0ASfmmXeOuTPealWio73fKZmHHfTYExu7NbT44ot72dWsiSzJr9XrrgtqKoqzTgU1TggCHfLo0UcfDS8adm/2plCKtZkiRxS/ypJGCCUleOCgyhs8EL7iudYsDUfMNDqwfPrpp3XBJHFibMlpzq04TTfPY/MSgoi6x9pmWl1kvbnfn4Vn/JBEkdMzjUc79/CVqKBmD4siQc0vFBEcARFIIas36n75hCAuTCppWl9cz1iTjAV9nKZXzvVboz5ZTuZO1hUFSQeKueeeO7UoWZ7X1Mw6ziyrV+LLps9xyOJUV7MNA23e7BHhTKAdwV3kQWgTjFTkN2q6Qk0k7BNBTZSdhBX76jHdwJuaNInEdT/ssMPC5ZprrhnOOYmdfwj0rN9t49ci8jzT7M+rv15zyimn+Ii/uoKiC377TV+86HY4RTNVQc1GVXHUX0gkJ0yp9GWJ7/fVOZoOLyHRchC4E6WYRWimsvQuPJbglXBe5QkOaPCOTVTKn6gxWXLoL4n+44NK09hIgMBQIY1pRzcPYmMrTAIaBUs7iFLNIvpU+ZCGVUm9TBpBTB2b2Qyp6rao2QW+inmyDKI1u0GyXNJH7tLXSsiFIvMrEcnMClDkUGIwgfAOdGJDMa1XfOwTQc1oRsi5BA54QcUUhI8t1mypJCsAdtpppxBuy8eFzSim2FtMeC9TmKSGI+u9/Qcc50ue82GqoIYP4cd4fZPES8feuHnECK0fB15klvIlNyHnRdHQ6jxe3X7GwKmCGhzYjYyQ6yRJhGjdzmKyNj53sE3mb/Yah9WSSy7pBz60dVYpxO8J5eLg0Q+I90WCFxqENe9S3J9grwIdEwptJXQbkqAqv4IEL3+S0E6x5yrJ+uWWV5soj04embWpghIPTp0sM8mbUHGlLNML30nZBQps6YAMaZbwh7HkLt5KgboVrWCDPzN5NHjqj3LFklTeJ5QtfY+arUdL6eLF2fF52kLteDE/IeBFJI3LXJAugio8k4rXZMrqI/wImaUcNvJJblQjH1NDkWykE4cyw4sNkwhmgM+5555bt5id5/ylhbWzu5w+1zSEjIs92vOT6VHdc02brBfp9RlH2sYGVvKR12TKVDvooIPqnmvavE2ZGhqeuCH7QASe8a6FcZ8RhNIMxbyoG1GbBAEQAEMbCPuO+1ZWwPiov5h3HPAig1v8qOE83gxHBG3d8+QmWcmQbRKzg6NiyJH3hgAPmdXUCLkG1/gdoe7iDKwrh4s4eAY+RAuyGRiBPKI9NWzYBR/5aOv4xHgXfSNxxG1e6LwI2tC+rGjgrIAXvgPFhn5Mkghv/7yorsl8XMd4pT3nXhyazXtCUJVSNwNe6EN2fFQsOLYScci7HPMg8EmUBG1SwzFNjjYkauJGn2jU0lBvp8bOI+GxQRtCG84i2c3NoT0lidHshBNO8Jvn6DP9pXS95oiWy/2sDYtIg1aF40+n8PwKRdovUaDZsUFO1s8Z4Zxk4xvstxBTpbS08qJ7GzDTql4iPOk4ZvltO4ijnifrKcLKyWBWp+Um07RzjfM5puQ1zzB3oeWoBx8tK0/TYraTZl+UQd2bV44//nhfJEu3+EsjEbJemyrrAEvj1cl7mPGU+Na6TbE2Tf+k9V+n64QGTWBPTMwyCG4qS6xswuSh+16jWbM/+9VXX+0djWX5NZu+/itoNpekK2ub0UXkcRFErGECQGBlEc4edjpLE9KaB9MCQh+PchphE086mtLqz9SLF5sd1BBAaYTZhul37MRMS4d9l53gmG4miXu77babfx7b5tPqRN40HkmezVwX2eGUB+kYoBBoeevFma4yCBWtaW9lyZzWhYFVl0MhHNMGPNJijsIskefMhBemlKxISVYRYDbBwZvllKQv2NGOj7VozXVWf2rbkuYwvV/VkV0D1elJvRdYYIFM1vQ1PoAyf8o7i6lsteDfc32eF4VM/ZARZf6SZlAtR4+yl7T3fyWFNIK7FSGtfPFJEM2ohJKAb4fvoWzAlvIoOg6E1p2WSMOo45+mSUtX1T1saTinKA9tTqYMpX9JBJAIPmAVAOsy4cGHW9b2pW1ikT6BAiz7wlsOJmXtUbSFdlEnOhRnCitK0gYuLbfXjvprMETwoYniA0CQtYprK+2jDs0GSmCLJFqQPwYJnLv8FUUKJutFcBbvI32HUGZAKhLOSR7dutbtUBEWSggotccySxgwYIA+CkeWxfFetktpYkQ2twqrKVDGsOfGhD+EbW+rINmbw8+GlRfXbG8QOzJ5Z9Gk8T9VQQyEKG4oK0ooE/fdd59ehu0o2pWjfWb6CC359wSHDgIg6QhMpsu7RojqR5mXrtlnaBc4stohtCoEvA587fDqq7wISBxt6mzri3o0K6SpGzMCnD5Zjqtm688yUNn83/81m6eX0hEABDE7LHKAkyZP405rF/s3561+iiNHjzrqqDQW4Z7stlk6WImZjw5EgdG/JygRrOZRQc1qMcx38Qw2mafsNYogszj2fdGVR51aVdMzgrosSJbeEDAE8hHAPsyKKn73r8jsxUxPV4fkc/3f06LIRMyIzITmmmuuQlPhqquuWjrghZmqCuq0GSq+JpbsMsvo1A8lIPhZroufiWOnQsx7xvTxv+63M0PAECiLQJrpAx6YAHDgZZnsMA9hdsRGjAZahogqxjyEkMyaMbJuWe3OSd6YKgkeg4rs+cm8XGt+2pYX/ZuWt1v3FJd+Y/roFnBWjiHwX0KgyI/QzBriLLwI5MoK5tI8eas8ELBZA4jmzzu2mz+Pd689a3nVR681xOpjCBgChkB/RcAEdX/tWWuXIWAI9BsETFD3m660hhgChkB/RcAEdX/tWWuXIWAI9BsETFD3m660hhgChkB/RcAEdX/tWWuXIWAI9BsETFD3m660hhgChkB/RaAw4KW/NtzaZQgYAoZAtxBoN+DFNOpu9ZSVYwgYAoZAiwhkatQt8rNshoAhYAgYAhUjYBp1xYAaO0PAEDAEqkbABHXViBo/Q8AQMAQqRsAEdcWAGjtDwBAwBKpGwAR11YgaP0PAEDAEKkbABHXFgBo7Q8AQMASqRsAEddWIGj9DwBAwBCpGwAR1xYAaO0PAEDAEqkbABHXViBo/Q8AQMAQqRsAEdcWAGjtDwBAwBKpGwAR11YgaP0PAEDAEKkbABHXFgBo7Q8AQMASqRsAEddWIGj9DwBAwBCpGwAR1xYAaO0PAEDAEqkbABHXViBo/Q8AQMAQqRsAEdcWAGjtDwBAwBKpG4P8AGsG0/KwH+LUAAAAASUVORK5CYII=)

```text
table {
  border-collapse: collapse;
}
```

### 隐藏单元格

![image-20190819142210720](http://houdunren.gitee.io/note/assets/img/image-20190819142210720.eb9c32b2.png)

```text
<style>
  table {
      empty-cells: hide;
  }
</style>
...

<table border="1">
        <tr>
            <td>在线教程</td>
            <td>houdunren.com</td>
        </tr>
        <tr>
            <td></td>
            <td>hdcms.com</td>
        </tr>
</table>
```

### 无边框表格

![image-20190820130113657](http://houdunren.gitee.io/note/assets/img/image-20190820130113657.fe67c238.png)

```text
<style>
        table {
            border: none;
            border-collapse: collapse;
        }

        table td {
            border: none;
            border-right: solid 1px #ddd;
            border-bottom: solid 1px #ddd;
        }

        table tr:first-child td {
            border-top: solid 1px #ddd;
        }

        table td:last-child {
            border-right: none;
        }
</style>
...
<table border="1">
        <thead>
            <tr>
                <td>编号</td>
                <td>标题</td>
                <td>网址</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>在线社区</td>
                <td>houdunren.com</td>
            </tr>
            <tr>
                <td>2</td>
                <td>开源系统</td>
                <td>hdcms.com</td>
            </tr>
        </tbody>
</table>
```

### 数据表格

可以为表格元素使用伪类控制样式，下例中使用 `hover` 伪类样式

![image-20190820152827000](http://houdunren.gitee.io/note/assets/img/image-20190820152827000.3ce6ee55.png)

```text
<style>
        table,
        td {
            border: none;
            font-size: 14px;
            border-collapse: collapse;
        }

        table tr:hover {
            background: #ddd;
            cursor: pointer;
        }

        table td {
            border-top: solid 1px #ccc;
            padding: 10px;
        }
</style>
    
<table border="1">
        <thead>
            <tr>
                <td>编号</td>
                <td>标题</td>
                <td>网址</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>在线社区</td>
                <td>houdunren.com</td>
            </tr>
            <tr>
                <td>2</td>
                <td>开源系统</td>
                <td>hdcms.com</td>
            </tr>
            <tr>
                <td>3</td>
                <td>开发实战</td>
                <td>houdunwang.com</td>
            </tr>
</table>
```

## 列表

### 列表符号

使用 `list-style-type` 来设置列表样式，规则是继承的，所以在`ul` 标签上设置即可。

| 值                   | 描述                                                        |
| :------------------- | :---------------------------------------------------------- |
| none                 | 无标记。                                                    |
| disc                 | 默认。标记是实心圆。                                        |
| circle               | 标记是空心圆。                                              |
| square               | 标记是实心方块。                                            |
| decimal              | 标记是数字。                                                |
| decimal-leading-zero | 0开头的数字标记。(01, 02, 03, 等。)                         |
| lower-roman          | 小写罗马数字(i, ii, iii, iv, v, 等。)                       |
| upper-roman          | 大写罗马数字(I, II, III, IV, V, 等。)                       |
| lower-alpha          | 小写英文字母The marker is lower-alpha (a, b, c, d, e, 等。) |
| upper-alpha          | 大写英文字母The marker is upper-alpha (A, B, C, D, E, 等。) |
| lower-greek          | 小写希腊字母(alpha, beta, gamma, 等。)                      |
| lower-latin          | 小写拉丁字母(a, b, c, d, e, 等。)                           |
| upper-latin          | 大写拉丁字母(A, B, C, D, E, 等。)                           |
| hebrew               | 传统的希伯来编号方式                                        |
| armenian             | 传统的亚美尼亚编号方式                                      |
| georgian             | 传统的乔治亚编号方式(an, ban, gan, 等。)                    |
| cjk-ideographic      | 简单的表意数字                                              |
| hiragana             | 标记是：a, i, u, e, o, ka, ki, 等。（日文片假名）           |
| katakana             | 标记是：A, I, U, E, O, KA, KI, 等。（日文片假名）           |
| hiragana-iroha       | 标记是：i, ro, ha, ni, ho, he, to, 等。（日文片假名）       |
| katakana-iroha       | 标记是：I, RO, HA, NI, HO, HE, TO, 等。（日文片假名）       |

隐藏列表符号

```text
ul {
  list-style-type: none;
}
```

自定义列表样式

```text
ul li {
  /* list-style-image: url(xj-small.png);
  list-style-image: radial-gradient(10px 10px, red, black); */
  
  list-style-image: linear-gradient(45deg, red, black);
}
```

### 符号位置

控制符号显示在内容外面还是内部

| 选项    | 说明 |
| ------- | ---- |
| inside  | 内部 |
| outside | 外部 |

```text
ul {
  list-style-position: inside;
}
```

### 组合定义

可以一次定义列表样式

```text
ul {
    list-style: circle inside;
}
```

### 背景符号

![image-20190819164427052](http://houdunren.gitee.io/note/assets/img/image-20190819164427052.dd5e42c1.png)

```text
ul li {
  background: url(xj-small.png) no-repeat 0 6px;
  background-size: 10px 10px;
  list-style-position: inside;
  list-style: none;
  text-indent: 15px;
}
```

多图背景定义

![image-20190820155342265](http://houdunren.gitee.io/note/css/assets/image-20190820155342265.png)

```text
<style>
        ul {
            list-style-type: none;
        }

        ul li {
            background-image: url(xj-small.png), url(houdunren.jpg);
            background-repeat: no-repeat, repeat;
            background-size: 10px 10px, 100%;
            background-position: 5px 7px, 0 0;
            text-indent: 20px;
            border-bottom: solid 1px #ddd;
            margin-bottom: 10px;
            padding-bottom: 5px;

        }
</style>
```

## 追加内容

### 基本使用

使用伪类 `::before` 向前添加内容，使用 `::after` 向后面添加内容。

```text
a::after {
  content: " (坚持努力) ";
}
```

### 提取属性

使用属性值添加内容，可以使用标准属性与自定义属性。

```text
<style>
  a::after {
    content: attr(href);
  }
</style>

<a href="houdunren.com">后盾人</a>
```

通过属性值添加标签提示

![image-20190819170234330](data:image/png;base64,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)

```text
a {
    position: relative;
}

a:hover {
    &::before {
        content: "URL: "attr(data-url);
        background: #555;
        color: white;
        position: absolute;
        top: 20px;
        padding: 3px 10px;
        border-radius: 10px;
    }
}
```

### 自定义表单

![image-20190820165451079](http://houdunren.gitee.io/note/css/assets/image-20190820165451079.png)

```text
<style>
        body {
            padding: 80px;
        }

        .field {
            position: relative;
        }

        input {
            border: none;
            outline: none;
        }

        .field::after {
            content: '';
            background: linear-gradient(to right, white, red, green, blue, white);
            height: 30px;
            position: relative;
            width: 100%;
            height: 1px;
            display: block;
            left: 0px;
            right: 0px;
        }

        .field:hover::before {
            content: attr(data-placeholder);
            position: absolute;
            top: -20px;
            left: 0px;
            color: #555;
            font-size: 12px;
        }
</style>

...
<div class="field" data-placeholder="请输入少于100字的标题">
        <input type="text" id="name">
    </div>
```
