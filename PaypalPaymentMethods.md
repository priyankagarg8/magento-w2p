<table cellpadding='5' border='1' cellspacing='0'>
<blockquote><thead align='center'>
<blockquote><tr>
<blockquote><th></th>
<th>Order created</th>
<th>Payment successful</th>
<th>Payment canceled</th>
<th>After invoice</th>
<th>After shipment</th>
</blockquote></tr>
</blockquote></thead>
<tbody align='center'>
<blockquote><tr>
<blockquote><td><b>Express Checkout</b></td>
<td><i>Simple</i></td>
<td>Processing | To Print</td>
<td>No order | Saved</td>
<td>Processing | To Print</td>
<td>Complete | Generated, Deleted</td>
</blockquote></tr>
<tr>
<blockquote><td><i>Virtual</i></td>
<td>Processing | To Print</td>
<td>No order | Saved</td>
<td>Complete | Deleted</td>
<td>--- | ---</td>
</blockquote></tr></blockquote></blockquote>

<blockquote><tr>
<blockquote><td><b>Standard Checkout</b></td>
<td><i>Simple</i></td>
<td>Pending Payment | Saved</td>
<td>Processing  | To Print</td>
<td>Cancelled | Deleted, not generated</td>
<td>Processing  | To Print</td>
<td>Complete | Generated, Deleted</td>
</blockquote></tr>
<tr>
<blockquote><td><i>Virtual</i></td>
<td>Pending Payment | Saved</td>
<td>Complete  | Generated, Deleted</td>
<td>Cancelled | Deleted, not generated</td>
<td>Complete | Delete</td>
<td>--- | ---</td>
</blockquote></tr>
</blockquote><blockquote></tbody>
<table></blockquote>

<ul><li><b>Express checkout</b> works before any order is created in Mage and is part of the checkout process.<br>
</li><li><b>Standard checkout</b> sits after the checkout and an order is generated in Mage even before the customer is asked to pay