---
title: HTML之表单与列表
date: 2020-05-16 21:54:02
tags: 
    - HTML
categories: 
    - 前端
    - 后盾人
---
## 表单

> [houdunren.com](https://www.houdunren.com/) @ 向军大叔

表单是服务器收集用户数据的方式。

### FORM

一般情况下表单项要放在 FORM 内提交。

```text
<form action="hd.php" method="POST">
	<fieldset>
		<legend>测试</legend>
		<input type="text">
	</fieldset>
</form>
```

| 属性   | 说明                 |
| ------ | -------------------- |
| action | 后台地址             |
| method | 提交方式 GET 或 POST |

### LABEL

使用 `label` 用于描述表单标题，当点击标题后文本框会获得焦点，需要保证使用的ID在页面中是唯一的。

```text
<form action="hd.php" method="POST" novalidate>
<label for="title">标题</label>
<input type="text" name="title" id="title">
</form>
```

> 也可以将文本框放在 `label` 标签内部，这样就不需要设置 id 与 for 属性了

### INPUT

文本框用于输入单行文本使用，下面是常用属性与示例。

| 属性        | 说明                                      |
| ----------- | ----------------------------------------- |
| type        | 表单类型默认为 `text`                     |
| name        | 后台接收字段名                            |
| required    | 必须输入                                  |
| placeholder | 提示文本内容                              |
| value       | 默认值                                    |
| maxlength   | 允许最大输入字符数                        |
| size        | 表单显示长度，一般用不使用而用 `css` 控制 |
| disabled    | 禁止使用，不可以提交到后台                |
| readonly    | 只读，可提交到后台                        |

```text
<form action="hd.php" method="POST" novalidate>
        <fieldset>
            <legend>文本框</legend>
            <input type="text" name="title" required placeholder="请输入标题" maxlength="5" value="" size="100">
        </fieldset>
</form>
```

### 其他类型

通过设置表单的 `type` 字段可以指定不同的输入内容。

| 类型     | 说明                         |
| -------- | ---------------------------- |
| email    | 输入内容为邮箱               |
| url      | 输入内容为URL地址            |
| password | 输入内容为密码项             |
| tel      | 电话号，移动端会调出数字键盘 |
| search   | 搜索框                       |
| hidden   | 隐藏表单                     |
| submit   | 提交表单                     |

### HIDDEN

隐藏表单用于提交后台数据，但在前台内容不显示所以在其上做用样式定义也没有意义。

```text
<input type="hidden" name="id" value="1">
```

### 提交表单

创建提交按钮可以将表单数据提交到后台，有多种方式可以提交数据如使用AJAX，或HTML的表单按钮。

1. 使用input构建提交按钮，如果设置了name值按钮数据也会提交到后台，如果有多个表单项可以通过些判断是哪个表单提交的。

   ```text
   <input type="submit" name="submit" value="提交表单">
   ```

2. 使用button也可以提交，设置type属性为`submit` 或不设置都可以提交表单。

   ```text
   <button type="submit">提交表单</button>
   ```

### 禁用表单

通过为表单设置 `disabled` 或 `readonly` 都可以禁止修改表单，但 `readonly`表单的数据可以提交到后台。

```text
<input type="text" name="web" value="houdunren.com" readonly>
```

### PATTERN

表单可以通过设置 `pattern` 属性指定正则验证，也可以使用各种前端验证库如 [formvalidator](http://www.formvalidator.net/#default-validators_custom) 或 [validator.js](https://github.com/validatorjs/validator.js)。

| 属性      | 说明                 |
| --------- | -------------------- |
| pattern   | 正则表达式验证规则   |
| oninvalid | 输入错误时触发的事件 |

```text
<form action="">
	<input type="text" name="username" pattern="[A-z]{5,20}" 
	oninvalid="validate('请输入5~20位字母的用户名')">
	<button>提交</button>
</form>
    
<script>
	function validate(message) {
		alert(message);
	}
</script>
```

### TEXTAREA

文本域指可以输入多行文本的表单，当然更复杂的情况可以使用编辑器如`ueditor、ckeditor`等。

| 选项 | 说明                            |
| ---- | ------------------------------- |
| cols | 列字符数（一般使用css控制更好） |
| rows | 行数（一般使用css控制更好）     |

![image-20190805214818055](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAfIAAACGCAYAAAAmVQizAAAMSWlDQ1BJQ0MgUHJvZmlsZQAASImVVwdYU8kWnltSSWiBCEgJvYlSpEsJoUUQkCrYCEkgocSQEETsLssquHYRARu6KqLoWgBZK+paF8HuWh6KqCjrYsGGypsUWNf93nvfO9839/45c85/SubeOwOATg1PKs1FdQHIkxTI4iNCWJNS01ikLkAAIwEV6AJ7Hl8uZcfFRQMoQ/e/y9sbAFHer7oouf45/19FTyCU8wFA4iDOEMj5eRAfBAAv4UtlBQAQfaDeemaBVImnQGwggwlCLFXiLDUuUeIMNa5U2STGcyDeDQCZxuPJsgDQboZ6ViE/C/Jo34LYVSIQSwDQIUMcyBfxBBBHQjwqL2+GEkM74JDxFU/W3zgzhjl5vKxhrK5FJeRQsVyay5v1f7bjf0termIohh0cNJEsMl5ZM+zbrZwZUUpMg7hXkhETC7E+xO/FApU9xChVpIhMUtujpnw5B/YMMCF2FfBCoyA2hThckhsTrdFnZIrDuRDDFYIWiQu4iRrfxUJ5WIKGs0Y2Iz52CGfKOGyNbwNPpoqrtD+tyElia/hviYTcIf43xaLEFHXOGLVQnBwDsTbETHlOQpTaBrMpFnFihmxkinhl/jYQ+wklESFqfmxapiw8XmMvy5MP1YstFom5MRpcVSBKjNTw7ObzVPkbQdwslLCThniE8knRQ7UIhKFh6tqxdqEkSVMv1iktCInX+L6S5sZp7HGqMDdCqbeC2FRemKDxxQML4IJU8+Mx0oK4RHWeeEY2b3ycOh+8CEQDDggFLKCAIwPMANlA3Nbb1At/qWfCAQ/IQBYQAheNZsgjRTUjgdcEUAz+gEgI5MN+IapZISiE+s/DWvXVBWSqZgtVHjngMcR5IArkwt8KlZdkOFoyeAQ14n9E58Ncc+FQzv1Tx4aaaI1GMcTL0hmyJIYRQ4mRxHCiI26CB+L+eDS8BsPhjvvgvkPZ/mVPeEzoIDwkXCd0Em5PFy+SfVMPC0wAnTBCuKbmjK9rxu0gqyceggdAfsiNM3ET4IKPhZHYeBCM7Qm1HE3myuq/5f5bDV91XWNHcaWglBGUYIrDt57aTtqewyzKnn7dIXWuGcN95QzPfBuf81WnBfAe9a0lthg7gJ3FTmLnsSNYE2Bhx7Fm7BJ2VImHV9Ej1SoaihavyicH8oj/EY+nianspNy13rXH9ZN6rkBYpHw/As4M6SyZOEtUwGLDN7+QxZXwR49iubu6+QKg/I6oX1OvmarvA8K88Jcu/wQAvmVQmfWXjmcNwOHHADDe/qWzfgUfjxUAHG3nK2SFah2uvBDg10kHPlHGwBxYAwdYjzvwAv4gGISB8SAWJIJUMA12WQTXswzMBHPAQlAKysEKsBZUgU1gK9gJ9oD9oAkcASfBr+AiaAfXwR24errBc9AH3oIBBEFICB1hIMaIBWKLOCPuiA8SiIQh0Ug8koqkI1mIBFEgc5DvkHJkFVKFbEHqkJ+Rw8hJ5DzSgdxGHiA9yCvkI4qhNNQANUPt0DGoD8pGo9BEdCqaheajxWgJugytRGvR3WgjehK9iF5HO9HnaD8GMC2MiVliLpgPxsFisTQsE5Nh87AyrAKrxRqwFvg/X8U6sV7sA07EGTgLd4ErOBJPwvl4Pj4PX4pX4TvxRvw0fhV/gPfhXwh0ginBmeBH4BImEbIIMwmlhArCdsIhwhn4NHUT3hKJRCbRnugNn8ZUYjZxNnEpcQNxL/EEsYPYRewnkUjGJGdSACmWxCMVkEpJ60m7ScdJV0jdpPdkLbIF2Z0cTk4jS8iLyBXkXeRj5CvkJ+QBii7FluJHiaUIKLMoyynbKC2Uy5RuygBVj2pPDaAmUrOpC6mV1AbqGepd6mstLS0rLV+tiVpirQValVr7tM5pPdD6QNOnOdE4tCk0BW0ZbQftBO027TWdTrejB9PT6AX0ZfQ6+in6ffp7bYb2aG2utkB7vna1dqP2Fe0XOhQdWx22zjSdYp0KnQM6l3V6dSm6drocXZ7uPN1q3cO6N3X79Rh6bnqxenl6S/V26Z3Xe6pP0rfTD9MX6Jfob9U/pd/FwBjWDA6Dz/iOsY1xhtFtQDSwN+AaZBuUG+wxaDPoM9Q3HGuYbFhkWG141LCTiTHtmFxmLnM5cz/zBvPjCLMR7BHCEUtGNIy4MuKd0UijYCOhUZnRXqPrRh+NWcZhxjnGK42bjO+Z4CZOJhNNZppsNDlj0jvSYKT/SP7IspH7R/5uipo6mcabzjbdanrJtN/M3CzCTGq23uyUWa850zzYPNt8jfkx8x4LhkWghdhijcVxi2csQxablcuqZJ1m9VmaWkZaKiy3WLZZDljZWyVZLbLaa3XPmmrtY51pvca61brPxsJmgs0cm3qb320ptj62Itt1tmdt39nZ26XY/WDXZPfU3siea19sX29/14HuEOSQ71DrcM2R6OjjmOO4wbHdCXXydBI5VTtddkadvZzFzhucO0YRRvmOkoyqHXXThebCdil0qXd5MJo5Onr0otFNo1+MsRmTNmblmLNjvrh6uua6bnO946bvNt5tkVuL2yt3J3e+e7X7NQ+6R7jHfI9mj5djnccKx24ce8uT4TnB8wfPVs/PXt5eMq8Grx5vG+907xrvmz4GPnE+S33O+RJ8Q3zn+x7x/eDn5Vfgt9/vT38X/xz/Xf5Px9mPE47bNq4rwCqAF7AloDOQFZgeuDmwM8gyiBdUG/Qw2DpYELw9+AnbkZ3N3s1+EeIaIgs5FPKO48eZyzkRioVGhJaFtoXphyWFVYXdD7cKzwqvD++L8IyYHXEikhAZFbky8ibXjMvn1nH7xnuPnzv+dBQtKiGqKuphtFO0LLplAjph/ITVE+7G2MZIYppiQSw3dnXsvTj7uPy4XyYSJ8ZNrJ74ON4tfk782QRGwvSEXQlvE0MSlyfeSXJIUiS1JuskT0muS36XEpqyKqVz0phJcyddTDVJFac2p5HSktO2p/VPDpu8dnL3FM8ppVNuTLWfWjT1/DSTabnTjk7Xmc6bfiCdkJ6Sviv9Ey+WV8vrz+Bm1GT08Tn8dfzngmDBGkGPMEC4SvgkMyBzVebTrICs1Vk9oiBRhahXzBFXiV9mR2Zvyn6XE5uzI2cwNyV3bx45Lz3vsERfkiM5PcN8RtGMDqmztFTame+Xvza/TxYl2y5H5FPlzQUGcMN+SeGg+F7xoDCwsLrw/czkmQeK9IokRZdmOc1aMutJcXjxT7Px2fzZrXMs5yyc82Aue+6Weci8jHmt863nl8zvXhCxYOdC6sKchb8tcl20atGb71K+aykxK1lQ0vV9xPf1pdqlstKbP/j/sGkxvli8uG2Jx5L1S76UCcoulLuWV5R/WspfeuFHtx8rfxxclrmsbbnX8o0riCskK26sDFq5c5XequJVXasnrG5cw1pTtubN2ulrz1eMrdi0jrpOsa6zMrqyeb3N+hXrP1WJqq5Xh1TvrTGtWVLzboNgw5WNwRsbNpltKt/0cbN4860tEVsaa+1qK7YStxZufbwtedvZn3x+qttusr18++cdkh2dO+N3nq7zrqvbZbpreT1ar6jv2T1ld/ue0D3NDS4NW/Yy95bvA/sU+579nP7zjf1R+1sP+BxoOGh7sOYQ41BZI9I4q7GvSdTU2Zza3HF4/OHWFv+WQ7+M/mXHEcsj1UcNjy4/Rj1WcmzwePHx/hPSE70ns052tU5vvXNq0qlrpyeebjsTdebcr+G/njrLPnv8XMC5I+f9zh++4HOh6aLXxcZLnpcO/eb526E2r7bGy96Xm9t921s6xnUcuxJ05eTV0Ku/XuNeu3g95nrHjaQbt25Oudl5S3Dr6e3c2y9/L/x94M6Cu4S7Zfd071XcN71f+y/Hf+3t9Oo8+iD0waWHCQ/vdPG7nj+SP/rUXfKY/rjiicWTuqfuT4/0hPe0P5v8rPu59PlAb+kfen/UvHB4cfDP4D8v9U3q634pezn4aulr49c73ox909of13//bd7bgXdl743f7/zg8+Hsx5SPTwZmfiJ9qvzs+LnlS9SXu4N5g4NSnoyn2gpgcKCZmQC82gEAPRXuHdoBoE5Wn/NUgqjPpioE/hNWnwVV4gXAjmAAkhYAEA33KBvhsIWYBu/KrXpiMEA9PIaHRuSZHu5qLho88RDeDw6+NgOA1ALAZ9ng4MCGwcHP22CytwE4ka8+XyqFCM8Gm8coUXv3C/Ct/BuksX9wSo4AMwAAAAlwSFlzAAAWJQAAFiUBSVIk8AAAFOxJREFUeAHtnQWsI8Ufx+fgcHd3OBwSCBY4NGjQYAEOCXI4QY6gh0uACwlB76EBgtuhAQIECy7B3d2doP3Pd//MZLpvt6/bdnvt7GeS9zrd0d/n1/S7M7MzHVazwRAgAAEIQAACEOhLApP0Za/pNAQgAAEIQAACCQGEnA8CBCAAAQhAoI8JIOR97Dy6DgEIQAACEEDI+QxAAAIQgAAE+pgAQt7HzqPrEIAABCAAAYSczwAEIAABCECgjwkg5H3sPLoOAQhAAAIQQMj5DEAAAhCAAAT6mABC3sfOo+sQgAAEIACB4c0iGDNmTLNZyQcBCEAAAhCAQA6BcePG5aS0dpkReWvcKAUBCEAAAhDoCQJNj8hHjBiRdHj06NE90XE6AQEIQAACEOgnAgMDA6V0lxF5KVipFAIQgAAEINAdAgh5dzjTCgQgAAEIQKAUAgh5KVipFAIQgAAEINAdAgh5dzjTCgQgAAEIQKAUAgh5KVipFAIQgAAEINAdAgh5dzjTCgQgAAEIQKAUAgh5KVipFAIQgAAEINAdAgh5dzjTCgQgAAEIQKAUAgh5KVipFAIQgAAEINAdAgh5dzjTCgQgAAEIQKAUAk0f0dpM63fccYd57rnnzCSTTGLGjh1rhg0b1kyxvstz++23m+eff95MNtlk5phjjum7/tNhCEAAAhCIh0BHhfy+++4z5513XkJHAjfppJPGQyqwZMKECeayyy7zdgZJRCEAAQhAAAJdJcDUeldx0xgEIAABCECgswQQ8s7ypDYIQAACEIBAVwkg5F3FTWMQgAAEIACBzhLompD/+eefLfe8nbItN/pfwb/++qvdKjpSvh0G//77r/n9998b9qNWq5l2bW23fF4HVa/610qQ7X///XcrRX2Zoez6559/2m7DN0YEAhCAQEECpQr5k08+aQ455BCz/PLLmymmmMLMMcccZvPNNzcvvPDCkN28+uqrzXbbbWcWWWQRX3bTTTc1Z555pvnjjz8yy48bN86sscYaZs0118xM18Uff/wxyaN8aiMrfPrpp+bAAw80K664opl88smTfu+2227mxhtvzMrurz3wwAO+7tdff91fT0dUl9ofM2ZMXZL6o+v6kzg89thjST8WX3xxz0D89MR8VkiXv/nmm83OO+9sZpxxRjP11FObK664oq7Yb7/9Zk455RSz0UYbmRlmmCGxVb7aY489zEsvvVSX17158803fR+V5/333092KKy22mpJ+emnnz7hf/3117siLb0+9dRTZs8990w+O/KBdkKob/o8ffnllw3rlP8OPfTQpJ964FK7C+RL1ffMM89klk3bJf+pDrFX++uss44566yzzC+//JKUl38uvfTS5DM600wzJW0svfTS5vTTT8/9fGY2zEUIQAAC7RKwI52mwvjx42v6axQOOOAADZuSv8cff9zH3bXw9dprr82s6ptvvqltvfXWDcsut9xytddee21Q+X322ceXG5T43wUrAj7PiSeeOCjbo48+Wpt99tl9nrDPitsv6truu+/u08MKZJPL/8QTT4RJdfGllloqyTdy5Mi662eccYYv//DDD/u4qzN8taJdV1ZvwvJWdAaVv/zyy30Z8XP9COsN4xdccIHP7yKyy+W54YYbagsvvLB/7667V/mjaLCj54SxqyPv9c4778ys2t681KabbrrcPqm+0047rWZH2XXlQ7uuueaa3M+APpsqu+++++a2se6669bsTEBd/byBAAQg0IyOtkKpo9vP7JekDxrlKdgv82QkpdHfdddd50dEo0ePNhtssIGZeeaZfRlFNIK85557kmv2CzkZHS6xxBLmo48+MjfddJN56623ktHi2muvbd577z0zzTTT1JVv580XX3xhrLj6KkaMGGG23377pI8aoQ0MDJijjjrKp5cZ0eyDgjitsMIK5ueffzb2RsGPxq2QmE022cRoNJgVDj/88OTy6quvblZZZZVkxGiFO7mmusTvq6++8nlkp2ZNdA6A7FTYb7/9khkR+SkraMZEYeONNzYbbrihGT58uHnooYeMZgIULrroIrPjjjvWMU0SGvzT9sWQ8ahRo8zKK69s3n77baNRvuuz+LzyyitGo2AXNANkhda9TfqkkbRmIzQSv+qqq5K0o48+2uizZW88fd4woj4raOZE7O+//36jMxIUZJtG95qNsDd85qCDDkq2Wco3bhbjwQcfTPJts802SRn+QQACECiVQLPq38ydRDgi16jo5ZdfrqteI5ktttjCj2TCEaIy3nvvvT5No24r3nXlf/3115oVD58nPaJud0R+8MEH+7q33XbbmtoLgxWDQSO1ML2TI3Lr9JqdXg6rT0aCm222me+jFaa69HBErvK33XZbXbp7c8IJJ/g6jjzyyJpGwWGwSwQ+XX4I08ORq9o499xzw6JJPOyHnaYflJ534euvv64bTdsburqsGuXa6W7ft1133dWnK23VVVf1afaGwKe5SGiXPp/ffvutS6ql7dJsQxjeeOMNX7fstjd5te+++y7MUrvkkkt8Hrs0U5fGGwhAAALN6GgrlPQQUVOhmQ6EQp41LauG7Pqu/7KzI6+6tjXVrC9J/dnRVV2ae/P999/Xfdnb9XKXVGtHyO3auW9bX/I//PCDrzeMXHnllT6f+hmGTgr5cccdF1bt408//bRvP30jEwpoOs1VoJsTx1ginZ5idvnsWrTP98gjj7jLdYJnR/uZU8j2wTrvo/Tyga8oI3LyySf7Nhv13y0JzDvvvL59OxPgy9oZgoza/38pbEO8XAiFXDdLWcGO1H0bWVP7uuFxbO0MRVYVXIMABCpMoBkdbQVPaQ+7rb/++vY7bXBYcskl/cUPP/zQxxV58cUXk/d2ZJVMB9cl/vdGD25putmFdB3uetFXPbTlgqaU9fBXVthhhx2SKdWstE5e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)

```text
<textarea name="content" cols="30" rows="3">houdunren.com</textarea>
```

### SELECT

下拉列表项可用于多个值中的选择。

| 选项     | 说明       |
| -------- | ---------- |
| multiple | 支持多选   |
| size     | 列表框高度 |
| optgroup | 选项组     |
| selected | 选中状态   |
| option   | 选项值     |

![image-20190805215509898](http://houdunren.gitee.io/note/assets/img/image-20190805215509898.b03e4555.png)

```text
<select name="lesson">
        <option value="">== 选择课程 ==</option>
        <optgroup label="后台">
            <option value="php">PHP</option>
            <option value="linux">LINUX</option>
            <option value="mysql">MYSQL</option>
        </optgroup>
        <optgroup label="前台">
            <option value="php">HTML</option>
            <option value="linux">JAVASCRIPT</option>
            <option value="mysql">CSS</option>
        </optgroup>
</select>
```

### RADIO

单选框指只能选择一个选项的表单，如性别的选择`男、女、保密` 只能选择一个。

| 选项    | 说明     |
| ------- | -------- |
| checked | 选中状态 |

![image-20190805214006476](data:image/png;base64,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pZVWMjfddFOw8+lE/ycwY8aMeKW3t9d8/fXX8boWOpdAP30+Nbtzv/32WzNo0KDsB/bhCH3ltg/wWjwU5ltssYV555134hQoQa655prxuhY6k4Cq0p3pV11VDgTmzJmTEMXu7m6JYg5cq5CEqtI5eOmss84yG264YcOUqJJRFcN22WUXM27cuIb7v/766+aOO+5ouI82FkvgtttuS5ygp6cnsa6VziUgYczBt0cddZTZfvvtG6aE0FlhHDlypEFMG9msWbMkjI0AFbyNtsR77rknPktXV5fZdddd43UtdDYBVaU727+6uhYJuKJIEqecckqLKemwKhJoS4nxs88+i3r3vv/+e/Prr7+av/76y/Tr188sv/zyZuWVV47acdZbbz2z6qqrVpFpx+e50/33zz//mBtvvDHhxwkTJiTWtdLZBIL1StPD9/bbb5sPP/zQ/Pnnn6morrXWWmaTTTYxgwcPTrV/qJ38Xmmq0RtttFHD07/44ovm008/jfZZZZVVzD777NNw/1dffTXR8N/uXulO8N9XX31l0nDEVwcddFDsH5ZvueWWeD2PhRVWWMGsttpqeSSlNAogEEQYv/jiC/Paa69FpUN7Df37949KhCuuuKIZMGBAdMP+/vvvZvHixeaXX36xu0X/hw4darbbbrvEb+1c8YUxRF7SPNBF5aMT/PfJJ58Y7qOy2MSJE81dd91VluwoHx6BwqvS77//vnnjjTfi01Jaopq89tprx7/5Cwgjb3eqbNjHH39sfvzxR7PjjjsahFQWjkCn+I+XrkwE0hIoVBj9h2rjjTeORLFZ5gYOHGiGDx9u1l13XfPBBx+Y7777ztAeSRVnt912M8suu2yzJIJuv/76681mm23W8JzXXXedefrpp6N99t9/f3Paaac13J9rveSSSxruU/TGpcV/RXNU+tUjUJgwfv7554YQFQwhYwQBnSlZqoR0xmy55ZaROJIepcZXXnnF7LzzzqUizVjaZuE6Dz30UJxnRB9xbGR0ALTTOs1/MLc1kHpcqW4TY2ptgw02MM8//7xZZpll7E9N/++5555x2zBtk9OnT695jGo+NbGU5sdChBHxo/PAPtwjRowwjPf9+++/W7rwYcOGRR02VK95YN99911DmrJiCHSi/2jHXn/99RsCu/baaxPbL7jggqaB++4BRFi4wwfHjx/f9Jzu8VouD4FC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)

```text
<input type="radio" name="sex" value="boy" id="boy">
<label for="boy">男</label>

<input type="radio" name="sex" value="girl" id="girl" checked>
<label for="girl">女</label>
```

### CHECKBOX

复选框指允许选择多个值的表单。

![image-20190805214322364](http://houdunren.gitee.io/note/assets/img/image-20190805214322364.e491d0cc.png)

```text
<fieldset>
        <legend>复选框</legend>
        <input type="checkbox" name="sex" value="boy" id="boy">
        <label for="boy">PHP</label>

        <input type="checkbox" name="sex" value="girl" id="girl" checked>
        <label for="girl">MYSQL</label>
</fieldset>
```

### 文件上传

文件上传有多种方式，可以使用插件或JS拖放上传处理。HTML本身也提供了默认上传的功能，只是上传效果并不是很美观。

| 选项     | 说明                                              |
| -------- | ------------------------------------------------- |
| multiple | 支持多选                                          |
| accept   | 允许上传类型 `.png,.psd` 或 `image/png,image/gif` |

![image-20190805220123718](http://houdunren.gitee.io/note/assets/img/image-20190805220123718.d3e269d1.png)

```text
<form action="" method="POST" enctype="multipart/form-data">
	<fieldset>
		<input type="file" name="icon" multiple="multiple" accept="image/png,image/gif">
	</fieldset>
	<button>保存</button>
</form>
```

### 日期与时间

| 属性 | 说明                                                |
| ---- | --------------------------------------------------- |
| step | 间隔：date 缺省是1天，week缺省是1周，month缺省是1月 |
| min  | 最小时间                                            |
| max  | 最大时间                                            |

**日期选择**

![image-20190814160102123](http://houdunren.gitee.io/note/assets/img/image-20190814160102123.3b5fc40d.png)

```text
<input type="date" step="5" min="2020-09-22" max="2025-01-15" name="datetime">
```

**周选择**

![image-20190814160020196](http://houdunren.gitee.io/note/assets/img/image-20190814160020196.d2aa5314.png)

```text
<input type="week">
```

**月份选择**

![image-20190814160135995](http://houdunren.gitee.io/note/assets/img/image-20190814160135995.d820b83d.png)

```text
<input type="month">
```

**日期与时间**

![image-20190814160532544](http://houdunren.gitee.io/note/assets/img/image-20190814160532544.09dda1e0.png)

```text
<input type="datetime-local" name="datetime">
```

### DATELIST

input表单的输入值选项列表

![image-20190814175611789](data:image/png;base64,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)

```text
<form action="" method="post">
  <input type="text" list="lesson">
  <datalist id="lesson">
    <option value="PHP">后台管理语言</option>
    <option value="CSS">美化网站页面</option>
    <option value="MYSQL">掌握数据库使用</option>
  </datalist>
</form>
```

### autocomplete

浏览器基于之前键入过的值，应该显示出在字段中填写的选项。

```text
<form action="">
  <input type="search" autocomplete="on" name="content" />
  <button>提交</button>
</form>
```

## 列表

列表的使用与`word` 等软件的列表概念相似，只不过是应用在网页展示中。

### 有序列表

有序列表是指有数字编号的列表项，可以使用`CSS`定义更多样式，具体请查看CSS章节。

![image-20190801233425533](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAa4AAABqCAYAAADk+7WMAAABfGlDQ1BJQ0MgUHJvZmlsZQAAKJFjYGAqSSwoyGFhYGDIzSspCnJ3UoiIjFJgv8PAzcDDIMRgxSCemFxc4BgQ4MOAE3y7xsAIoi/rgsxK8/x506a1fP4WNq+ZclYlOrj1gQF3SmpxMgMDIweQnZxSnJwLZOcA2TrJBUUlQPYMIFu3vKQAxD4BZIsUAR0IZN8BsdMh7A8gdhKYzcQCVhMS5AxkSwDZAkkQtgaInQ5hW4DYyRmJKUC2B8guiBvAgNPDRcHcwFLXkYC7SQa5OaUwO0ChxZOaFxoMcgcQyzB4MLgwKDCYMxgwWDLoMjiWpFaUgBQ65xdUFmWmZ5QoOAJDNlXBOT+3oLQktUhHwTMvWU9HwcjA0ACkDhRnEKM/B4FNZxQ7jxDLX8jAYKnMwMDcgxBLmsbAsH0PA4PEKYSYyjwGBn5rBoZt5woSixLhDmf8xkKIX5xmbARh8zgxMLDe+///sxoDA/skBoa/E////73o//+/i4H2A+PsQA4AJHdp4IxrEg8AABx3SURBVHgB7Z0J2FXT98fXW1TKUMakRCJEymMow0OmZAopJErJGEKZMkUe8UgeDYZSUTIlQ4RCmVXi0aAklZQGmTKP57++62ed/7n3nvu+9763bve+fdfz3Pfss886++zz2ffd6+691967JFARCgmQAAmQAAkUCYFKRZJPZpMESIAESIAEjAANF78IJEACJEACRUWAhquoiouZJQESIAESoOHid4AESIAESKCoCNBwFVVxMbMkQAIkQAI0XPwOkAAJkAAJFBUBGq6iKi5mlgRIgARIgIaL3wESIAESIIGiIkDDVVTFxcySAAmQAAnQcPE7QAIkQAIkUFQEaLiKqriYWRIgARIgARoufgdIgARIgASKigANV1EVFzNLAiRAAiRAw8XvAAmQAAmQQFERoOEqquJiZkmABEiABDbaUBH8/fffsnjxYlm4cKE0a9ZMttlmm5xQ/Pjjj7Js2TJZunSpVKpUSY466qiM0xs8eLBUqVJFunXrlvE9VCQBEiCBDZVASUXaSBLG6Oeff5ZffvlFfvrpJwv78dtvv5UvvvhC5s6dK7NmzZL58+eHZQ6D8dBDD4XnCCCtKVOmyK+//mofTxdpe/owUkhz0aJF9rxoAgsWLJBddtklGpU23KhRI9liiy1k2rRpaXV4gQRIgARI4H8E1muLC5svP/LII7J8+XK57rrrci6TjTfeOKM09txzT2nfvr00btxYdtttN8F5svz+++9y9NFHJ0eH59tuu62sWrVKNttsMzn11FNlp512kh133NE+O+ywg9StWzfULSsAI1mtWrWy1HidBEiABEhACaw3w/Xbb7/JBRdcIKNGjbKCWBuGCwnBCHXu3FmqV68uW265pWy11VZSq1YtC+N88803l8qVK9szM/nTtWtXueGGG8yw1KhRw9L1+5HWscceKyNHjswkqbQ6aM0hvxQSIAESIIGyCeTdcKGSHjhwoNx7773WYik7i9lpNG3aVHr16pXdTaVor1692roW41TQDfn111/L+PHj4y7LEUccITB2pQladmi5scVVGiVeIwESIIH/J5D3MS6M4xx44IHSpEkT6d+/v7W64CCBbsNcpaSkRDp06CCPPfZYrknZ+Bi6AXORzz//XBo2bFhqEhhzQyuxQYMGNl5WqjIvkgAJkAAJ5L+rEN11jz76qBkY73Jbm+UwZswYee2118qVJAxocgsJ3Y5XX311Snpz5syRdu3aSZ8+feyYoqARGPMqS2DcIHg2jNgee+xR1i28TgIkQAIbNIG8dxWiBVJWKySXEoHTRIsWLcqVRFyrD+nBmHz44YcJrcKVK1faM6pWrWqts+gD69WrJ7Vr145GpQ3DWLlMmDCBhsth8EgCJEACaQjk3XClyUfO0XD2gLRp0ybFtT3XxDEut//++8cmc+2116bE9+3bV3r37p0Snxzx77//yvDhwy0aBnLs2LFy1VVXJavxnARIgARIIEKgwhguTP6FwC19bUhc66tjx47SvXv3tMnDWaM0F/rkG1999VWbTwbX/EMOOUQuu+wymTx5srRs2TJZleckQAIkQAL/EagwhmvJkiX2SjvvvLMd77jjDpk+fXpGBd2pUydrqUWVV6xYYadwp3dBC+n777/305QjDFc2MmDAAFPv2bOnTVaG4UIY+cbqGxQSIAESIIFUAhXOcNWvX9/ecurUqfL8888LuuBKE7iiN2/ePEUFK2JAouNxcPzAZ23IW2+9JZMmTZJWrVqF3ZBXXHGFwJg99dRTcsYZZ6yNxzANEiABEqhwBCrMz3pvcSV78sGJIt3nzTffTFugbri8BQdFjGf5ElBxR8zpykSQ1xNO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Iqv8YQB0TKfc7+GVarTLzRNzo4HneqsIXXZx4q0jN1x+ju67OEHLyw2Jp61jXymqXrm/+eabCdcWL15slXu0ReitMFT4V199daDjcIGOsSXcl+4EBhaG748//khRgXFduXJloONYds110XUaJ3gPpOWtK2esY24J6qNHjza9OEbOPuEGnpAACZBAjgTy4lWoFWAomKulv84FHoVwVPjggw/MAeGee+4JdcobqF69esqt22+/vcUpJ9FuOgtvt912KXqIgNNFVNSw2Gn9+vWj0WG4Zs2asvXWW4fnCNSuXTvhHCfVqlWzuBo1aiRcq1q1asI5TjDfTceiZNNNN5W77rrLHDJw/7nnniuYVpBO4HAyf/58UYMnVapUSVHbeOON7domm2xiDhuu63lLvqFhw4YW5Qz8OvIVFb8/OR46ceURvZdhEiABEigPgXVuuOBJBzf46667LjZ/Op5iXnNYQWPNmjWxOmsrslatWpYUvPbiBB6DUdl8883tFB6A+RJU9r179zYjhfzAuMNzb+TIkebxl2xIPF+VKlUSbbkKeJclrqvjimlVtaVl15xZWkVeIAESIIE8E1jnhgu/8KdMmWKu4nEGAC2h1atX22ujVbAuxVtOM2fOFK+Yo8+DG31UdtllFzuFW3uyaNejNGrUyOakxb1Xsn4m5x9//LHoWJTAnR2C9OFyD9dz7b60lum4cePSJgW3f7jPx60iouNellekD1EnCzvimckCt3iUGSS5FWqR/EMCJEAC65HAOjdceDd0C0LQ6oKhigqWfMIvfx3bERg5iHoEWgWObsS1KWjNqCu8JemToj19ddawOUh+jmOLFi2se00dGES98aKXbLUPdLdhblVcN1mCcoYnMDo333yzdO/ePYWTJ6FemRaMY6QejnYNxgldhy4Io/sR0rJlSzvquJsdUSbJrTSdFmAGUD0py70MlyXOPyRAAiSwLgjkOEaW0e0Y4PeBehwxRwju8HCV1neyDzzZXLTitjjoZiLuOBCnC/dtPMNd2eEO7s+EizscMAYOHGj5cy9Bd85Aeph/BX1cwzwvnawbuPce4uGqDnHnjLZt29p59A+eA124pUdl+fLlFu/OGXCq8HlQ8HAEo4cffticWDzPPictjhEcLdzpQn8sBCNGjLA8R9PEdAQI3ORbtWplzwcjTAeAvpcJnEPc8QT66RjDZR55wzSDZPG8JMfznARIgARyIZA3r0K4vHul6JUwjvCi87lF/iJwucY1eB1mIqVVkM2bN7e03HAhPRhJr8w9L/Cimzp1qulGDRf0dTWIhInAuAcVedT9HhORER9nuJAeriUbLhgGxEfnOsElHkYH8dEPjHjUFT0dI3g6+tyz6P1gmexiD09DnwAe1UV+tPsWrx5KOsbqTGL5jDNcPh8sTIQBEiABElgLBEqQhlZaeROtWAUOBui+gufaFltsEftsbX1InNddrHI5IzG2tmDBAhtLysQJActIwTOxTp06NvZT3tXsM8kuxuCwHBWKB56KarhSlqQqjRG6/9zZBGN17mgS92yM16HbE0tb7b777vQGjIPEOBIggYIhkHfDVTBvzoyQAAmQAAkUJYG8OGcUJRlmmgRIgARIoCAJ0HAVZLEwUyRAAiRAAukI0HClI8N4EiABEiCBgiRAw1WQxcJMkQAJkAAJpCNAw5WODONJgARIgAQKkgANV0EWCzNFAiRAAiSQjgANVzoyjCcBEiABEihIAjRcBVkszBQJkAAJkEA6AjRc6cgwngRIgARIoCAJ0HAVZLEwUyRAAiRAAukI0HClI8N4EiABEiCBgiRAw1WQxcJMkQAJkAAJpCNAw5WODONJgARIgAQKkgANV0EWCzNFAiRAAiSQjgANVzoyjCcBEiABEihIAv8H5p+qrvkLp5AAAAAASUVORK5CYII=)

```text
<style>
        .li-style1{
            /* 
            circle      空心圆
            disc        实心圆
            square      实心方块
            decimal     数字
            upper-alpha 大写字母
            lower-alpha 小写字母
            upper-roman 大写罗马数字
            lower-roman 小写罗马数字
             */
            list-style-type: decimal;
        }
        
        .li-style2{
        	/* 取消风格 */
            list-style: none;
        }
        .li-style3{
        	/*inside 内部 outside 外部（默认）*/
        	list-style-position: inside;
        }
</style>

<ol start="1">
	<li>后盾人</li>
	<li>houdunren.com</li>
	<li>hdcms.com</li>
</ol>
```

### 无序列表

没有数字编号的列表项，可以使用`CSS`定义更多样式，具体请查看CSS章节。

![image-20190801233519967](data:image/png;base64,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)

```text
<ul>
	<li>后盾人</li>
	<li>houdunren.com</li>
	<li>hdcms.com</li>
</ul>
```

### 描述列表

描述列表指每个列表项有单独的标题。

![image-20190801234034944](http://houdunren.gitee.io/note/assets/img/image-20190801234034944.93d22fad.png)

```text
<dl>
	<dt>开源产品</dt>
	<dd>hdcms内容管理系统</dd>
	<dd>hdjs前库组件库</dd>
	
	<dt>网站导航</dt>
	<dd>houdunren.com</dd>
	<dd>houdunwang.com</dd>
</dl>
```
