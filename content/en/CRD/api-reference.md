---
title: Api Reference
weight: -1
---
<p>Packages:</p>
<ul>
<li>
<a href="#policy.kcloudlabs.io%2fv1alpha1">policy.kcloudlabs.io/v1alpha1</a>
</li>
</ul>
<h2 id="policy.kcloudlabs.io/v1alpha1">policy.kcloudlabs.io/v1alpha1</h2>
Resource Types:
<ul><li>
<a href="#policy.kcloudlabs.io/v1alpha1.ClusterOverridePolicy">ClusterOverridePolicy</a>
</li><li>
<a href="#policy.kcloudlabs.io/v1alpha1.ClusterValidatePolicy">ClusterValidatePolicy</a>
</li><li>
<a href="#policy.kcloudlabs.io/v1alpha1.OverridePolicy">OverridePolicy</a>
</li></ul>
<h3 id="policy.kcloudlabs.io/v1alpha1.ClusterOverridePolicy">ClusterOverridePolicy
</h3>
<div>
<p>ClusterOverridePolicy represents the cluster-wide policy that overrides a group of resources.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiVersion</code><br/>
string</td>
<td>
<code>
policy.kcloudlabs.io/v1alpha1
</code>
</td>
</tr>
<tr>
<td>
<code>kind</code><br/>
string
</td>
<td><code>ClusterOverridePolicy</code></td>
</tr>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.OverridePolicySpec">
OverridePolicySpec
</a>
</em>
</td>
<td>
<p>Spec represents the desired behavior of ClusterOverridePolicy.</p>
<br/>
<br/>
<table>
<tr>
<td>
<code>resourceSelectors</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceSelector">
[]ResourceSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ResourceSelectors restricts resource types that this override policy applies to.
nil means matching all resources.</p>
</td>
</tr>
<tr>
<td>
<code>overrideRules</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.RuleWithOperation">
[]RuleWithOperation
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>OverrideRules defines a collection of override rules on target operations.</p>
</td>
</tr>
</table>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ClusterValidatePolicy">ClusterValidatePolicy
</h3>
<div>
<p>ClusterValidatePolicy represents the cluster-wide policy that validate a group of resources.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiVersion</code><br/>
string</td>
<td>
<code>
policy.kcloudlabs.io/v1alpha1
</code>
</td>
</tr>
<tr>
<td>
<code>kind</code><br/>
string
</td>
<td><code>ClusterValidatePolicy</code></td>
</tr>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ClusterValidatePolicySpec">
ClusterValidatePolicySpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>resourceSelectors</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceSelector">
[]ResourceSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ResourceSelectors restricts resource types that this validate policy applies to.
nil means matching all resources.</p>
</td>
</tr>
<tr>
<td>
<code>validateRules</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ValidateRuleWithOperation">
[]ValidateRuleWithOperation
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>ValidateRules defines a collection of validate rules on target operations.</p>
</td>
</tr>
</table>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.OverridePolicy">OverridePolicy
</h3>
<div>
<p>OverridePolicy represents the policy that overrides a group of resources.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiVersion</code><br/>
string</td>
<td>
<code>
policy.kcloudlabs.io/v1alpha1
</code>
</td>
</tr>
<tr>
<td>
<code>kind</code><br/>
string
</td>
<td><code>OverridePolicy</code></td>
</tr>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.OverridePolicySpec">
OverridePolicySpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>resourceSelectors</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceSelector">
[]ResourceSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ResourceSelectors restricts resource types that this override policy applies to.
nil means matching all resources.</p>
</td>
</tr>
<tr>
<td>
<code>overrideRules</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.RuleWithOperation">
[]RuleWithOperation
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>OverrideRules defines a collection of override rules on target operations.</p>
</td>
</tr>
</table>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.AffectMode">AffectMode
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ValidateCondition">ValidateCondition</a>)
</p>
<div>
<p>AffectMode is defining match affect</p>
</div>
<h3 id="policy.kcloudlabs.io/v1alpha1.ClusterValidatePolicySpec">ClusterValidatePolicySpec
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ClusterValidatePolicy">ClusterValidatePolicy</a>)
</p>
<div>
<p>ClusterValidatePolicySpec defines the desired behavior of ClusterValidatePolicy.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>resourceSelectors</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceSelector">
[]ResourceSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ResourceSelectors restricts resource types that this validate policy applies to.
nil means matching all resources.</p>
</td>
</tr>
<tr>
<td>
<code>validateRules</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ValidateRuleWithOperation">
[]ValidateRuleWithOperation
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>ValidateRules defines a collection of validate rules on target operations.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.Cond">Cond
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ValidateCondition">ValidateCondition</a>)
</p>
<div>
<p>Cond is validation condition for validator</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Equal&#34;</p></td>
<td><p>CondEqual - <code>Equal</code></p>
</td>
</tr><tr><td><p>&#34;Exist&#34;</p></td>
<td><p>CondExist - <code>Exist</code></p>
</td>
</tr><tr><td><p>&#34;Gt&#34;</p></td>
<td><p>CondGreater - <code>Gt</code></p>
</td>
</tr><tr><td><p>&#34;Gte&#34;</p></td>
<td><p>CondGreaterOrEqual - <code>Gte</code></p>
</td>
</tr><tr><td><p>&#34;In&#34;</p></td>
<td><p>CondIn - <code>In</code></p>
</td>
</tr><tr><td><p>&#34;Lt&#34;</p></td>
<td><p>CondLesser - <code>Lt</code></p>
</td>
</tr><tr><td><p>&#34;Lte&#34;</p></td>
<td><p>CondLesserOrEqual - <code>Lte</code></p>
</td>
</tr><tr><td><p>&#34;NotEqual&#34;</p></td>
<td><p>CondNotEqual - <code>NotEqual</code></p>
</td>
</tr><tr><td><p>&#34;NotExist&#34;</p></td>
<td><p>CondNotExist - <code>NotExist</code></p>
</td>
</tr><tr><td><p>&#34;NotIn&#34;</p></td>
<td><p>CondNotIn - <code>NotIn</code></p>
</td>
</tr><tr><td><p>&#34;Regex&#34;</p></td>
<td><p>CondRegex match regex. e.g. <code>/^\d{1,}$/</code></p>
</td>
</tr></tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ConstantValue">ConstantValue
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.OverrideRuleTemplate">OverrideRuleTemplate</a>, <a href="#policy.kcloudlabs.io/v1alpha1.ValidateCondition">ValidateCondition</a>)
</p>
<div>
<p>ConstantValue defines exact types. Only one of field can be set.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>string</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>String as a string</p>
</td>
</tr>
<tr>
<td>
<code>integer</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>Integer as an integer(int64)</p>
</td>
</tr>
<tr>
<td>
<code>float</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.Float64">
Float64
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Float as float but use string to store, so please provide in comma (e.g. float: &ldquo;1.2&rdquo;)</p>
</td>
</tr>
<tr>
<td>
<code>boolean</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Boolean only true or false can be recognized.</p>
</td>
</tr>
<tr>
<td>
<code>stringSlice</code><br/>
<em>
[]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>StringSlice as a slice of string(e.g. [&ldquo;a&rdquo;,&ldquo;b&rdquo;])</p>
</td>
</tr>
<tr>
<td>
<code>integerSlice</code><br/>
<em>
[]int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>IntegerSlice as a slice of integer(int64) (e.g. [1,2,3])</p>
</td>
</tr>
<tr>
<td>
<code>floatSlice</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.Float64">
[]Float64
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>FloatSlice as a slice of float but using string (e.g. [&ldquo;1.2&rdquo;, &ldquo;2.3&rdquo;])</p>
</td>
</tr>
<tr>
<td>
<code>stringMap</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>StringMap as key-value set and both are string.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.FieldSelector">FieldSelector
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ResourceSelector">ResourceSelector</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>matchFields</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>matchFields is a map of {key,value} pairs. A single {key,value} in the matchFields
map is equivalent to an element of matchExpressions, whose key field is &ldquo;key&rdquo;, the
operator is &ldquo;In&rdquo;, and the values array contains only &ldquo;value&rdquo;.</p>
</td>
</tr>
<tr>
<td>
<code>matchExpressions</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.FieldSelectorRequirement">
[]FieldSelectorRequirement
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>matchExpressions is a list of fields selector requirements. The requirements are ANDed.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.FieldSelectorRequirement">FieldSelectorRequirement
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.FieldSelector">FieldSelector</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>field</code><br/>
<em>
string
</em>
</td>
<td>
<p>Field is the field key that the selector applies to.
Must provide whole path of key, such as <code>metadata.annotations.uid</code></p>
</td>
</tr>
<tr>
<td>
<code>operator</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#labelselectoroperator-v1-meta">
Kubernetes meta/v1.LabelSelectorOperator
</a>
</em>
</td>
<td>
<p>operator represents a key&rsquo;s relationship to a set of values.
Valid operators are In, NotIn, Exists and DoesNotExist.</p>
</td>
</tr>
<tr>
<td>
<code>value</code><br/>
<em>
[]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>values is an array of string values. If the operator is In or NotIn,
the values array must be non-empty. If the operator is Exists or DoesNotExist,
the values array must be empty.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.Float64">Float64
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ConstantValue">ConstantValue</a>, <a href="#policy.kcloudlabs.io/v1alpha1.ResourcesOversellRule">ResourcesOversellRule</a>)
</p>
<div>
<p>Float64 is alias for float64 as string</p>
</div>
<h3 id="policy.kcloudlabs.io/v1alpha1.HttpDataRef">HttpDataRef
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ResourceRefer">ResourceRefer</a>)
</p>
<div>
<p>HttpDataRef defines a http request essential params</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>url</code><br/>
<em>
string
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>URL as whole http url</p>
</td>
</tr>
<tr>
<td>
<code>method</code><br/>
<em>
string
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Method as basic http method(e.g. GET or POST)</p>
</td>
</tr>
<tr>
<td>
<code>header</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Header represents the custom header added to http request header.</p>
</td>
</tr>
<tr>
<td>
<code>params</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Params represents the query value for http request.</p>
</td>
</tr>
<tr>
<td>
<code>body</code><br/>
<em>
k8s.io/apiextensions-apiserver/pkg/apis/apiextensions/v1.JSON
</em>
</td>
<td>
<em>(Optional)</em>
<p>Body represents the json body when http method is POST.</p>
</td>
</tr>
<tr>
<td>
<code>auth</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.HttpRequestAuth">
HttpRequestAuth
</a>
</em>
</td>
<td>
<p>Auth defines basic info for get authorization token before do request.
Note: it will request authURL with post and <code>Header.Set(&quot;Authorization&quot;, &quot;Basic &quot;+basicAuth(username, password))</code>
and get token from response body. Response Body must be a valid json and contains token like this: `{&ldquo;token&rdquo;: &ldquo;xxx&rdquo;} .
After get the token, the request will add a new key value to header, key is &ldquo;Authorization&rdquo; and value is &ldquo;Bearer xxx&rdquo;.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.HttpRequestAuth">HttpRequestAuth
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.HttpDataRef">HttpDataRef</a>)
</p>
<div>
<p>HttpRequestAuth defines basic info for get auth token from remote api</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>staticToken</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>StaticToken represents for static token for call api instead of get token from remote api.
StaticToken and other fields are mutually exclusive, staticToken is priority to take effect.</p>
</td>
</tr>
<tr>
<td>
<code>username</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Username represents username for auth.</p>
</td>
</tr>
<tr>
<td>
<code>password</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Password represents Password for auth.</p>
</td>
</tr>
<tr>
<td>
<code>authUrl</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>AuthURL represents remote url to request and get token.</p>
</td>
</tr>
<tr>
<td>
<code>expireDuration</code><br/>
<em>
<a href="https://pkg.go.dev/k8s.io/apimachinery/pkg/apis/meta/v1#Duration">
Kubernetes meta/v1.Duration
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ExpireDuration is providing for some auth api won&rsquo;t return exact expire time, so can you this field set
an expiry duration for token</p>
</td>
</tr>
<tr>
<td>
<code>token</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Token stores the latest token get from AuthURL, and it&rsquo;ll be updated when token expired.
This filed is not fill by user, so don&rsquo;t edit it.</p>
</td>
</tr>
<tr>
<td>
<code>expireAt</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#time-v1-meta">
Kubernetes meta/v1.Time
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ExpireAt sores the token expire time. Same as above field, this field also updated automatically.
This filed is not fill by user, so don&rsquo;t edit it.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.OperationType">OperationType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ValueProcess">ValueProcess</a>)
</p>
<div>
<p>OperationType defines the type of processing value.</p>
</div>
<h3 id="policy.kcloudlabs.io/v1alpha1.OverridePolicySpec">OverridePolicySpec
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ClusterOverridePolicy">ClusterOverridePolicy</a>, <a href="#policy.kcloudlabs.io/v1alpha1.OverridePolicy">OverridePolicy</a>)
</p>
<div>
<p>OverridePolicySpec defines the desired behavior of OverridePolicy.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>resourceSelectors</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceSelector">
[]ResourceSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ResourceSelectors restricts resource types that this override policy applies to.
nil means matching all resources.</p>
</td>
</tr>
<tr>
<td>
<code>overrideRules</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.RuleWithOperation">
[]RuleWithOperation
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>OverrideRules defines a collection of override rules on target operations.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.OverrideRuleTemplate">OverrideRuleTemplate
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.Overriders">Overriders</a>)
</p>
<div>
<p>OverrideRuleTemplate represents a single template of rule definition</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.OverrideRuleType">
OverrideRuleType
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Type represents current rule operate field type.</p>
</td>
</tr>
<tr>
<td>
<code>operation</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.OverriderOperator">
OverriderOperator
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Operation represents current operation type.</p>
</td>
</tr>
<tr>
<td>
<code>path</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Path is field path of current object(e.g. <code>/spec/affinity</code>)
If current type is annotations or labels, then only need to provide the key, no need whole path.</p>
</td>
</tr>
<tr>
<td>
<code>value</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ConstantValue">
ConstantValue
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Value sets exact value for rule, like enum or numbers
Must set value when type is regex.</p>
</td>
</tr>
<tr>
<td>
<code>valueRef</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceRefer">
ResourceRefer
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ValueRef represents for value reference from current or remote object.
Need specify the type of object and how to get it.</p>
</td>
</tr>
<tr>
<td>
<code>resources</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#resourcerequirements-v1-core">
Kubernetes core/v1.ResourceRequirements
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Resources valid only when the type is <code>resources</code></p>
</td>
</tr>
<tr>
<td>
<code>resourcesOversell</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourcesOversellRule">
ResourcesOversellRule
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ResourcesOversell valid only when the type is <code>resourcesOversell</code></p>
</td>
</tr>
<tr>
<td>
<code>tolerations</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#toleration-v1-core">
[]Kubernetes core/v1.Toleration
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Tolerations valid only when the type is <code>tolerations</code></p>
</td>
</tr>
<tr>
<td>
<code>affinity</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#affinity-v1-core">
Kubernetes core/v1.Affinity
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Affinity valid only when the type is <code>affinity</code></p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.OverrideRuleType">OverrideRuleType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.OverrideRuleTemplate">OverrideRuleTemplate</a>)
</p>
<div>
<p>OverrideRuleType is definition for type of single override rule template</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;affinity&#34;</p></td>
<td><p>OverrideRuleTypeAffinity - <code>affinity</code></p>
</td>
</tr><tr><td><p>&#34;annotations&#34;</p></td>
<td><p>OverrideRuleTypeAnnotations - <code>annotations</code></p>
</td>
</tr><tr><td><p>&#34;labels&#34;</p></td>
<td><p>OverrideRuleTypeLabels - <code>labels</code></p>
</td>
</tr><tr><td><p>&#34;resources&#34;</p></td>
<td><p>OverrideRuleTypeResources - <code>resources</code></p>
</td>
</tr><tr><td><p>&#34;resourcesOversell&#34;</p></td>
<td><p>OverrideRuleTypeResourcesOversell - <code>resourcesOversell</code></p>
</td>
</tr><tr><td><p>&#34;tolerations&#34;</p></td>
<td><p>OverrideRuleTypeTolerations - <code>tolerations</code></p>
</td>
</tr></tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.OverriderOperator">OverriderOperator
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.OverrideRuleTemplate">OverrideRuleTemplate</a>, <a href="#policy.kcloudlabs.io/v1alpha1.PlaintextOverrider">PlaintextOverrider</a>)
</p>
<div>
<p>OverriderOperator is the set of operators that can be used in an overrider.</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;add&#34;</p></td>
<td><p>OverriderOpAdd - &ldquo;add&rdquo; value to object</p>
</td>
</tr><tr><td><p>&#34;remove&#34;</p></td>
<td><p>OverriderOpRemove - remove field form object</p>
</td>
</tr><tr><td><p>&#34;replace&#34;</p></td>
<td><p>OverriderOpReplace - remove and add value(if specified path doesn&rsquo;t exist, it will add directly)</p>
</td>
</tr></tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.Overriders">Overriders
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.RuleWithOperation">RuleWithOperation</a>)
</p>
<div>
<p>Overriders offers various alternatives to represent the override rules.</p>
<p>If more than one alternative exist, they will be applied with following order:
- RenderCue
- Cue
- Plaintext</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>plaintext</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.PlaintextOverrider">
[]PlaintextOverrider
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Plaintext represents override rules defined with plaintext overriders.</p>
</td>
</tr>
<tr>
<td>
<code>cue</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Cue represents override rules defined with cue code.</p>
</td>
</tr>
<tr>
<td>
<code>template</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.OverrideRuleTemplate">
OverrideRuleTemplate
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Template of rule which defines override rule, and
it will be rendered to CUE and store in RenderedCue field, so
if there are any data added manually will be erased.</p>
</td>
</tr>
<tr>
<td>
<code>renderedCue</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>RenderedCue represents override rule defined by Template.
Don&rsquo;t modify the value of this field, modify Rules instead of.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.PlaintextOverrider">PlaintextOverrider
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.Overriders">Overriders</a>)
</p>
<div>
<p>PlaintextOverrider is a simple overrider that overrides target fields
according to path, operator and value.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>path</code><br/>
<em>
string
</em>
</td>
<td>
<p>Path indicates the path of target field</p>
</td>
</tr>
<tr>
<td>
<code>op</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.OverriderOperator">
OverriderOperator
</a>
</em>
</td>
<td>
<p>Operator indicates the operation on target field.
Available operators are: add, update and remove.</p>
</td>
</tr>
<tr>
<td>
<code>value</code><br/>
<em>
k8s.io/apiextensions-apiserver/pkg/apis/apiextensions/v1.JSON
</em>
</td>
<td>
<em>(Optional)</em>
<p>Value to be applied to target field.
Must be empty when operator is Remove.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ResourceRefer">ResourceRefer
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.OverrideRuleTemplate">OverrideRuleTemplate</a>, <a href="#policy.kcloudlabs.io/v1alpha1.ValidateCondition">ValidateCondition</a>)
</p>
<div>
<p>ResourceRefer defines different types of ref data</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>from</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ValueRefFrom">
ValueRefFrom
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>From represents where this referenced object are.</p>
</td>
</tr>
<tr>
<td>
<code>path</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Path has different meaning, it represents current object field path like &ldquo;/spec/replica&rdquo; when From equals &ldquo;current&rdquo;
and it also can be format like &ldquo;data.result.x.y&rdquo; when From equals &ldquo;http&rdquo;, it represents the path in http response
Only when From is owner(means refer current object owner), the path can be empty.</p>
</td>
</tr>
<tr>
<td>
<code>k8s</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceSelector">
ResourceSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>K8s means refer another object from current cluster.</p>
</td>
</tr>
<tr>
<td>
<code>http</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.HttpDataRef">
HttpDataRef
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Http means refer data from remote api.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ResourceSelector">ResourceSelector
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ClusterValidatePolicySpec">ClusterValidatePolicySpec</a>, <a href="#policy.kcloudlabs.io/v1alpha1.OverridePolicySpec">OverridePolicySpec</a>, <a href="#policy.kcloudlabs.io/v1alpha1.ResourceRefer">ResourceRefer</a>)
</p>
<div>
<p>ResourceSelector the resources will be selected.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>apiVersion</code><br/>
<em>
string
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>APIVersion represents the API version of the target resources.</p>
</td>
</tr>
<tr>
<td>
<code>kind</code><br/>
<em>
string
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Kind represents the Kind of the target resources.</p>
</td>
</tr>
<tr>
<td>
<code>namespace</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Namespace of the target resource.
Default is empty, which means inherit from the parent object scope.</p>
</td>
</tr>
<tr>
<td>
<code>name</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Name of the target resource.
Default is empty, which means selecting all resources.</p>
</td>
</tr>
<tr>
<td>
<code>labelSelector</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#labelselector-v1-meta">
Kubernetes meta/v1.LabelSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>A label query over a set of resources.
If name is not empty, labelSelector will be ignored.</p>
</td>
</tr>
<tr>
<td>
<code>fieldSelector</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.FieldSelector">
FieldSelector
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>A field query over a set of resources.
If name is not empty, fieldSelector wil be ignored.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ResourcesOversellRule">ResourcesOversellRule
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.OverrideRuleTemplate">OverrideRuleTemplate</a>)
</p>
<div>
<p>ResourcesOversellRule defines factor of resource oversell</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>cpuFactor</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.Float64">
Float64
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>CpuFactor factor of cup oversell, it is float number less than 1, the range of value is (0,1.0)</p>
</td>
</tr>
<tr>
<td>
<code>memoryFactor</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.Float64">
Float64
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>MemoryFactor factor of cup oversell, it is float number less than 1, the range of value is (0,1.0)</p>
</td>
</tr>
<tr>
<td>
<code>diskFactor</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.Float64">
Float64
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>DiskFactor factor of cup oversell, it is float number less than 1, the range of value is (0,1.0)</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.RuleWithOperation">RuleWithOperation
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.OverridePolicySpec">OverridePolicySpec</a>)
</p>
<div>
<p>RuleWithOperation defines the override rules on operations.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>targetOperations</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#operation-v1-admission">
[]Kubernetes admission/v1.Operation
</a>
</em>
</td>
<td>
<p>TargetOperations is the operations the admission hook cares about - CREATE, UPDATE, DELETE, CONNECT or *
for all of those operations and any future admission operations that are added.
If &lsquo;*&rsquo; is present, the length of the slice must be one.
Required.</p>
</td>
</tr>
<tr>
<td>
<code>overriders</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.Overriders">
Overriders
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Overriders represents the override rules that would apply on resources</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ValidateCondition">ValidateCondition
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ValidateRuleTemplate">ValidateRuleTemplate</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>affectMode</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.AffectMode">
AffectMode
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>AffectMode represents the mode of policy hit affect, in default case(reject), webhook rejects the operation when
policy hit, otherwise it will allow the operation.
If mode is <code>allow</code>, only allow the operation when policy hit, otherwise reject them all.</p>
</td>
</tr>
<tr>
<td>
<code>cond</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.Cond">
Cond
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Cond represents type of condition (e.g. Equal, Exist)</p>
</td>
</tr>
<tr>
<td>
<code>dataRef</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceRefer">
ResourceRefer
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>DataRef represents for data reference from current or remote object.
Need specify the type of object and how to get it.</p>
</td>
</tr>
<tr>
<td>
<code>message</code><br/>
<em>
string
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Message specify reject message when policy hit.</p>
</td>
</tr>
<tr>
<td>
<code>value</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ConstantValue">
ConstantValue
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Value sets exact value for rule, like enum or numbers</p>
</td>
</tr>
<tr>
<td>
<code>valueRef</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ResourceRefer">
ResourceRefer
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ValueRef represents for value reference from current or remote object.
Need specify the type of object and how to get it.</p>
</td>
</tr>
<tr>
<td>
<code>valueProcess</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ValueProcess">
ValueProcess
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ValueProcess represents handle process for value or valueRef.
Currently only support for number value, so make sure value or value from remote is a number.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ValidateRuleTemplate">ValidateRuleTemplate
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ValidateRuleWithOperation">ValidateRuleWithOperation</a>)
</p>
<div>
<p>ValidateRuleTemplate defines template for validate rule</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ValidateRuleType">
ValidateRuleType
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Type represents current rule operate field type.</p>
</td>
</tr>
<tr>
<td>
<code>condition</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ValidateCondition">
ValidateCondition
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Condition represents general condition rule for more custom demand.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ValidateRuleType">ValidateRuleType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ValidateRuleTemplate">ValidateRuleTemplate</a>)
</p>
<div>
<p>ValidateRuleType is definition for type of single validate rule template</p>
</div>
<h3 id="policy.kcloudlabs.io/v1alpha1.ValidateRuleWithOperation">ValidateRuleWithOperation
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ClusterValidatePolicySpec">ClusterValidatePolicySpec</a>)
</p>
<div>
<p>ValidateRuleWithOperation defines validate rules on operations.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>targetOperations</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#operation-v1-admission">
[]Kubernetes admission/v1.Operation
</a>
</em>
</td>
<td>
<p>Operations is the operations the admission hook cares about - CREATE, UPDATE, DELETE, CONNECT or *
for all of those operations and any future admission operations that are added.
If &lsquo;*&rsquo; is present, the length of the slice must be one.
Required.</p>
</td>
</tr>
<tr>
<td>
<code>cue</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Cue represents validate rules defined with cue code.</p>
</td>
</tr>
<tr>
<td>
<code>template</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.ValidateRuleTemplate">
ValidateRuleTemplate
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Template of condition which defines validate cond, and
it will be rendered to CUE and store in RenderedCue field, so
if there are any data added manually will be erased.</p>
</td>
</tr>
<tr>
<td>
<code>renderedCue</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>RenderedCue represents validate rule defined by Template.
Don&rsquo;t modify the value of this field, modify Rules instead of.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ValueProcess">ValueProcess
</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ValidateCondition">ValidateCondition</a>)
</p>
<div>
<p>ValueProcess defines operation to handle value to compare.
E.g. operation: &lsquo;*&rsquo;
operationWith: 50%  # or 0.5</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>operation</code><br/>
<em>
<a href="#policy.kcloudlabs.io/v1alpha1.OperationType">
OperationType
</a>
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>Operation defines the type of operate value, and it should work with operationWith.
For example, operation is <code>*</code> and operationWith is 0.5 then in cue the value will be multiplied by 0.5.</p>
</td>
</tr>
<tr>
<td>
<code>operationWith</code><br/>
<em>
k8s.io/apimachinery/pkg/util/intstr.IntOrString
</em>
</td>
<td>
<em>(<code>Required</code>)</em>
<p>OperationWith defines value for operate to handle static value or value from remote.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ValueRefFrom">ValueRefFrom
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#policy.kcloudlabs.io/v1alpha1.ResourceRefer">ResourceRefer</a>)
</p>
<div>
<p>ValueRefFrom defines where the override value comes from when value is refer other object or http response</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;current&#34;</p></td>
<td><p>FromCurrentObject means read data from current k8s object(the newest one when update operate intercept)</p>
</td>
</tr><tr><td><p>&#34;http&#34;</p></td>
<td><p>FromHTTP - read data from http response</p>
</td>
</tr><tr><td><p>&#34;k8s&#34;</p></td>
<td><p>FromK8s - read data from other object in current kubernetes</p>
</td>
</tr><tr><td><p>&#34;old&#34;</p></td>
<td><p>FromOldObject means read data from old object, only used when object be updated</p>
</td>
</tr></tbody>
</table>
<h3 id="policy.kcloudlabs.io/v1alpha1.ValueType">ValueType
(<code>string</code> alias)</h3>
<div>
<p>ValueType defines whether value is specified by user or refer from other object</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;const&#34;</p></td>
<td><p>ValueTypeConst means value is specified exactly.</p>
</td>
</tr><tr><td><p>&#34;ref&#34;</p></td>
<td><p>ValueTypeRefer means value is refer from other object</p>
</td>
</tr></tbody>
</table>
<hr/>
<p><em>
Generated with <code>gen-crd-api-reference-docs</code>
.
</em></p>
