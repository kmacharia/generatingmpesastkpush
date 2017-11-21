<h1>Generating an M-Pesa STK (Simtoolkit) push on Safaricom line</h1>
M-Pesa STK push is an easy way of making Lipa na M-pesa payment.

Request is initiated from a USSD, Mobile app or any form of web request. All a user is required to do is provide their M-pesa PIN and voila, a C2B mpesa transaction is complete.

First [generate your access token](https://github.com/kmacharia/darajaaccesstoken).

Set your request headers

![setting request headers](https://github.com/kmacharia/generatingmpesastkpush/blob/master/stk-push-headers.png)

[Get your test credentials](https://developer.safaricom.co.ke/test_credentials) and [parameter definitions](https://developer.safaricom.co.ke/lipa-na-m-pesa-online/apis/post/stkpush/v1/processrequest).

Note: use code provided under Lipa Na Mpesa Online Shortcode for your shortcode.

Make a POST request to:

`https://sandbox.safaricom.co.ke/mpesa/stkpush/v1/processrequest`

with parameters:

`{
    "BusinessShortCode": "Shortcode (6 digits)",
    "Password": "base64.encode(ShortcodePasskeyTimestamp)",
    "Timestamp": "yyyymmddhhiiss",
    "TransactionType": "CustomerPayBillOnline",
    "Amount": "10",
    "PartyA": "MSISDN (12 digits)",
    "PartyB": "Shortcode (6 digits)",
    "PhoneNumber": "MSISDN (12 digits)",
    "CallBackURL": "https://callbackurl",
    "AccountReference": "123456",
    "TransactionDesc": "Testing"
}
`

Sample request:

![sample lipa na mpesa online request](https://github.com/kmacharia/generatingmpesastkpush/blob/master/generate-lipa-na-mpesa-web-request.png)

Check your phone asking you to provide M-Pesa PIN to complete transaction:

![STK push on phone](https://github.com/kmacharia/generatingmpesastkpush/blob/master/stk-push-on-phone.png)
