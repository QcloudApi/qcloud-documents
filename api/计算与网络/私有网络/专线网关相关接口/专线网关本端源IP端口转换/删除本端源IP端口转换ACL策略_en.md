## 1. API Description

This API (DeleteLocalSourceIPPortTranslationAclRule) is used to delete the ACL rules for local IP port translation.
Domain for API request:<font style="color:red">vpc.api.qcloud.com</font>


## 2. Input Parameters
The following request parameter list only provides API request parameters. Common request parameters need to be added when the API is called. For more information, refer to <a href="/doc/api/372/4153" title="Common request parameters">Common Request Parameters</a>. The Action field for this API is DeleteLocalSourceIPPortTranslationAclRule.

| Parameter Name | Required | Type | Description |
|---------|---------|---------|---------|
| vpcId | Yes | String | Virtual private cloud ID assigned by the system, for example: vpc-dfg5445.  |
| directConnectGatewayId | Yes | String | Direct Connect gateway ID assigned by the system, for example: dcg-4d545d.  |
| translationIPPool | Yes | String | Mapped IP pool, for example: 11.1.1.1-11.1.1.10.  |
| aclRules.n | Yes | Array | ID array of ACL rules, for example: aclRules.0=25.  |

## 3. Output Parameters

| Parameter Name | Type | Description |
|---------|---------|---------|
| code | Int | Common error code; 0: Succeeded; other values: Failed. For more information, please refer to <a href="https://www.qcloud.com/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#1.E3.80.81.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81" title="Common Error Codes">Common Error Codes</a> on the Error Code page. |
| message | String | Module error message description depending on API. |

 ## 4. Error Code Table
 The following error code list only provides the business logic error codes for this API. For additional common error codes, refer to <a href="https://www.qcloud.com/doc/api/245/4924" title="VPC Error Codes">VPC Error Codes</a>.
 
| Error code | Description |
|---------|---------|
| InvalidVpc.NotFound | Invalid VPC. VPC resource does not exist. Please verify that the resource information you entered is correct. This can be queried via the <a href="https://www.qcloud.com/doc/api/245/%e5%88%9b%e5%bb%ba%e7%a7%81%e6%9c%89%e7%bd%91%e7%bb%9c?viewType=preview" title="Querying Virtual Private Cloud List">Query Virtual Private Cloud List</a> (DescribeVpcEx) API. |
| InvalidDirectConnectGateway.NotFound | Invalid Direct Connect gateway. Direct Connect gateway resource does not exist. Please verify that the resource information you entered is correct. This can be queried via the <a href="https://www.qcloud.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%b8%93%e7%ba%bf%e7%bd%91%e5%85%b3?viewType=preview" title="Querying Direct Connect Gateway">Query Direct Connect Gateway</a> (DescribeDirectConnectGateway) API. |
| InvalidLocalSourceIPPortTranslation.NotFound | Invalid local IP port translation rules. Local IP port translation rule does not exist. Please verify that the resource information you entered is correct. |

## 5. Example
Input
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=DeleteLocalSourceIPPortTranslationAclRule
&<<a href="https://www.qcloud.com/doc/api/229/6976">Common request parameters</a>>
&vpcId=vpc-dfgg190
&directConnectGatewayId=dcg-ddf14d
&translationIPPool=11.1.1.1-11.1.1.10
&aclRules.0=25
</pre>
Output
```
{
    "code":"0",
    "message":""
}
```


