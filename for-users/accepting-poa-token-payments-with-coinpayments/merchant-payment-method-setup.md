---
description: 设置购物车插件，网站按钮，API连接或POS
---

# 商户付款方式设置

![&#x5546;&#x5BB6;&#x4ED8;&#x6B3E;&#x754C;&#x9762;](../../.gitbook/assets/merchant_setup.png)

### 购物车插件

插件可用于大多数电子商务应用程序。 该列表位于：[https://www.coinpayments.net/merchant-tools-plugins](https://www.coinpayments.net/merchant-tools-plugins)

### 自定义按钮创建器

创建一个可以嵌入网站的html按钮。 填写表格，然后单击“**生成按钮**”以接收您的自定义按钮。

![&#x81EA;&#x5B9A;&#x4E49;&#x6309;&#x94AE;&#x5F62;&#x5F0F;](../../.gitbook/assets/button_form.png)

示例生成的按钮输出。 （[请参阅此处的所有HTML POST字段](https://www.coinpayments.net/merchant-tools-buttons)。）

```text
<form action="https://www.coinpayments.net/index.php" method="post">
	<input type="hidden" name="cmd" value="_pay">
	<input type="hidden" name="reset" value="1">
	<input type="hidden" name="merchant" value="e49ad0bd4052d7c38c8d9dfa8949f914">
	<input type="hidden" name="item_name" value="Donation">
	<input type="hidden" name="item_number" value="1">
	<input type="hidden" name="currency" value="USD">
	<input type="hidden" name="amountf" value="1.00000000">
	<input type="hidden" name="quantity" value="1">
	<input type="hidden" name="allow_quantity" value="1">
	<input type="hidden" name="want_shipping" value="0">
	<input type="hidden" name="allow_extra" value="1">
	<input type="image" src="https://www.coinpayments.net/images/pub/buynow-med-grey.png" alt="Buy Now with CoinPayments.net">
</form>
```

### API, IPNs和更多

提供自定义集成的说明。 从这里开始 [https://www.coinpayments.net/merchant-tools-ipn](https://www.coinpayments.net/merchant-tools-ipn)

### 销售点（POS）亲自付款

这是接受亲自付款的首选方法。

* 对于预填充版本（包含目的和收费金额），请使用POS界面生成链接/ QR码。

![&#x9884;&#x5148;&#x586B;&#x5199;&#x7684;POS&#x8868;&#x5355;&#x3002; &#x7528;&#x6237;&#x53EF;&#x4EE5;&#x8F93;&#x5165;&#x94FE;&#x63A5;&#x6216;&#x626B;&#x63CF;QR&#x7801;&#x4EE5;&#x5B8C;&#x6210;&#x4ED8;&#x6B3E;&#x3002;](../../.gitbook/assets/pos1.png)

* 商家信息中心也提供Quick POS。 这将打开一个带有付款计算器的新标签。

![&#x5F00;&#x542F;Quick POS](../../.gitbook/assets/quick_pos.png)

* 输入付款金额，然后单击**继续**。

![&#x8F93;&#x5165;&#x91D1;&#x989D;&#xFF0C;&#x7136;&#x540E;&#x5355;&#x51FB;&#x7EE7;&#x7EED;](../../.gitbook/assets/quick_pos2.png)

* 选择POA20令牌作为付款方式，然后单击“**完成付款**”

![&#x9009;&#x62E9;POA20](../../.gitbook/assets/quick_pos3.png)

* 向客户显示付款屏幕。 他们可以使用支持POA20的[移动钱包应用程序](https://www.poa.network/v/zhong-wen/for-users/wallets)扫描QR码，然后输入付款所需的金额。

![&#x751F;&#x6210;&#x7684;QR&#x7801;&#xFF0C;&#x5BA2;&#x6237;&#x5C06;&#x6C47;&#x6B3E;&#x5230;&#x8BE5;&#x5730;&#x5740;&#x3002;](../../.gitbook/assets/quick_pos4.png)

## 

