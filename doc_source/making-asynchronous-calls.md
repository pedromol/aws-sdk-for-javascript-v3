--------

This is a preview version of the Developer Guide for the AWS SDK for JavaScript Version 3 \(V3\)\.

A preview version of the AWS SDK for JavaScript V3 is available on [Github](https://github.com/aws/aws-sdk-js-v3)\.

Help us improve the AWS SDK for JavaScript documentation by providing feedback using the **Feedback** link, or create an issue or pull request on [GitHub](https://github.com/awsdocs/aws-sdk-for-javascript-v3)\.

--------

# Managing asychronous calls<a name="making-asynchronous-calls"></a>

For example, the home page of an e\-commerce website lets returning customers sign in\. Part of the benefit for customers who sign in is that, after signing in, the site then customizes itself to their particular preferences\. To make this happen:

1. The customer must log in and be validated with their user name and password\.

1. The customer's preferences are requested from a customer database\.

1. The database provides the customer's preferences that are used to customize the site before the page loads\.

If these tasks execute synchronously, then each must finish before the next can start\. The webpage would be unable to finish loading until the customer preferences return from the database\. However, after the database query is sent to the server, receipt of the customer data can be delayed or even fail due to network bottlenecks, exceptionally high database traffic, or a poor mobile device connection\.

To keep the website from freezing under those conditions, call the database asychronously\. After the database call executes, sending your asynchronous request, your code continues to execute as expected\. If you don't properly manage the response of an asynchronous call, your code can attempt to use information it expects back from the database when that data isn't available yet\.

![\[Showing difference between synchronous and asynchronous execution.\]](http://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/images/async-vs-sync.png)