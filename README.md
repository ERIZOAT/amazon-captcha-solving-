# Best Amazon AWS WAF captcha solving service

## Bonus Code
 A bonus code for Capsolver: **AMN**. After redeeming it, you will get an extra 5% bonus after each recharge, Unlimited

![image](https://github.com/ERIZOAT/amazon-captcha-solving-/assets/157081315/43b5deae-00e7-4c67-8806-25208acc4046)

## What is Amazon AWS WAF captcha?
AWS WAF CAPTCHA is a security feature provided by Amazon Web Services (AWS) designed to protect websites and applications from automated bot attacks by incorporating CAPTCHA challenges. CAPTCHA, which stands for Completely Automated Public Turing test to tell Computers and Humans Apart, is a type of challenge-response test used to determine whether the user is human.

This feature enhances the AWS Web Application Firewall (WAF) by allowing web administrators to set up rules that require users to solve CAPTCHA puzzles before their requests are processed. This is particularly useful for mitigating automated threats such as web scraping, credential stuffing, and layer 7 Distributed Denial-of-Service (DDoS) attacks.

![image](https://github.com/ERIZOAT/amazon-captcha-solving-/assets/157081315/05fd20eb-8685-4512-9658-bff07c401aad)

## Solving AWS WAF captcha by Using CapSolver
Enter [Capsolver](https://www.capsolver.com/), a leading captcha solving service that specializes in resolving various types of captchas, including those used by AWS WAF. 


To solve AWS WAF Captcha issues, please follow our [documentation](https://docs.capsolver.com/guide/captcha/awsWaf.html) as a priority. In this example we will use only the required parameters. the task types for AWS WAF Captcha are as follows:  

-  ``AntiAwsWafTaskProxyless``: This task type requires don't require your own proxy.
- ``AntiAwsWafTask``: This task type requires your own proxies.

In this case, the task type that will be used in this blog, will be `AntiAwsWafTaskProxyLess`.

###  Step 1: Submit the information to Capsolver

```http
POST https://api.capsolver.com/createTask
{
 "clientKey":"yourapiKey",
 "task":
 {
 "type":"AntiAwsWafTaskProxyless",
 "websiteURL":"https://efw47fpad9.execute-api.us-east-1.amazonaws.com/latest",
  "awsKey":"key value",
  "awsIv":"iv value",
  "awsContext":"context value",
  "awsChallengeJS":"Url of the js challenge"
 }
}
```
This will return a response that contains `taskId`, save this value and submit to the step 2.

### Step 2: Get the results
We will need to retrieve the ``getTaskResult`` method until the captcha is solved. Retrieve every 3-5s.
```http
POST https://api.capsolver.com/getTaskResult
Host: api.capsolver.com
Content-Type: application/json
{
 "clientKey":"YOUR_API_KEY",
 "taskId": "TASKID OF CREATETASK" //ID created by the createTask method
}
```
Captcha solution will look like:
![AWS CAPTCHA TOKEN SOLUTION](https://assets.capsolver.com/prod/images/post/2023-07-12/925dd643-d8b9-4a7b-923c-f0b0c897e04e.png)

After the captcha has been solved, you need to create the cookie ``aws-waf-token`` and add the value that you got from capsolver response.

## Documentation 
[Capsolver API documentation](https://docs.capsolver.com/guide/api-server.html)
