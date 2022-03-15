![SageSevdLogoGreen](https://raw.githubusercontent.com/SagePayments/Sage-Exchange-Virtual-Desktop/master/logo-sage-exchange-virtual-desktop-@2x.png)
![SageSevdUI](https://developer.sagepayments.com/sites/default/files/paymentsolutions-virtual-desktop_v1.png)
---

# Paya Exchange Virtual Desktop (PEVD) / formerly called Sage Exchange Virtual Desktop (SEVD)

 
PEVD/SEVD GitHub sample repo and documentation - https://github.com/SagePayments/Sage-Exchange-Virtual-Desktop

PEVD operates as a redirect. We do not support PEVD within an iframe. You create an XML request a and submit using an html Form POST.
 
## Server Side Operation:
**Build Request Envelope** - https://www.sageexchange.com/sevd/frmenvelope.aspx

This endpoint will allow you to submit your initial unencoded XML request and returns an encoded envelope. 

## Client Side Operation:
**Submit Payment Request Envelope** - https://www.sageexchange.com/sevd/frmpayment.aspx

This endpoint will allow you to submit your encoded envelope to initiate the payment or vault form. When your user completes their interaction with the form PEVD will return an encoded response envelope.

## Server Side Operation:
**Open Response Envelope** - https://www.sageexchange.com/sevd/frmopenenvelope.aspx

This endpoint will allow you to submit your encoded response envelope and returns the unencoded XML for your consumption. The data is returned to your redirect or through a postback if you include a postback URL.

## Enable CAPTCHA

Adding an "Enable_Captcha" to <input> and set the value to "true" to enable CAPTCHA within the PEVD form.

### Example html form with CAPTCHA enabled
```xml
<html>
  <body onload="document.frm1.submit()">
    <form method="POST" action="https://www.sageexchange.com/sevd/frmPayment.aspx" name="frm1">
      <input type="hidden" name="request" value="<?php echo htmlspecialchars($tokenizedRequest) ?>" />
      <input type="hidden" name="redirect_url" value="<?php echo "https://$redirectUrl" ?>" />
      <input type="hidden" name="consumer_initiated" value="true" />
      <input type="hidden" name="Enable_Captcha" value="true" />
    </form>
  </body>
</html>
```
