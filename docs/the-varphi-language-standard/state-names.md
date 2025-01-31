# State Names

A state name in Varphi starts with the letter `q`, followed by at least one alphanumeric character or underscore (`_`).

Examples of valid state names include:

* `q0`
* `qzero`
* `q_My_State_`
* `q_my_state__`

{% hint style="info" %}
The lexer uses the following pattern to match state names:

<pre data-full-width="true"><code><strong>q[a-zA-Z0-9_]+
</strong></code></pre>
{% endhint %}
