# JiraGitLabAPI
##  Jira
Jira的API有多种认证方式，最简单的是用Basic Auth的方式，请参考<br>
https://developer.atlassian.com/cloud/jira/platform/jira-rest-api-basic-authentication/
<br>
简单来说就是把用户名密码按user:password的方式做base64加密，然后设置在HTTP头部即可<br>
node.js代码例
<pre><code>var request = require("request");
var jiraoptions ={ method: 'POST',
    url: 'http://jiurl:jiraport/rest/api/2/issue/'+issueid+'/transitions',
    headers: {'Content-Type': 'application/json',
        Authorization: 'Basic 加密后的user:password==' },
    body: { 请求主体 },
    json: true };
request(jiraoptions, function (error, response, body) {
    if (error) throw new Error(error);
    res.status(200).end();
});</code></pre>

API文档请参考<br>
https://docs.atlassian.com/DAC/rest/jira/6.1.html#d2e1074

##  Gitlab
Gitlab可以使用private token的方式，token可以在settings->access token里发行，在HTTP请求头里加上'PRIVATE-TOKEN': 'access token'即可
<br>
node.js代码例
<pre><code>var request = require("request");
var options = {
        method: 'POST',
        url: 'http://gitlaburl:gitlabport/api/v4/projects/29/repository/branches',
        headers:{'PRIVATE-TOKEN': 'accesstoken'},
        formData: { 请求参数 };
request(options, function (error, response, body) {
    if (error) throw new Error(error);
});</code></pre>
API文档请参考<br>
https://docs.gitlab.com/ee/api/README.html
