# Instructions for my.properties
This file contains all variables that we will need ton run our SCAN Against a target




# Extra authentication parameters

```
auth.loginurl             The URL to the login page. Required.
auth.username             A valid username. Required.
auth.password             A valid password. Required.
auth.otpsecret            The OTP secret.
auth.bearer_token         A Bearer token to use in the authorization header for each request.
auth.username_field       The HTML name or id attribute of the username field.
auth.password_field       The HTML name or id attribute of the password field.
auth.submit_field         The HTML name or id attribute of the submit field.
auth.otp_field            The HTML name or id attribute of the OTP field.
auth.first_submit_field   The HTML name or id attribute of the first submit field (in case of username -> next page -> password -> submit).
auth.submitaction         "Click" or "Submit" to click the login button or submit the form.
auth.display              True or False, indicate if the the webdriver should run in Headless mode.
auth.exclude              Comma separated list of excluded URL's (regex). Default: (logout|uitloggen|afmelden|signout)
auth.include              Comma separated list of included URL's (regex). Default: only the target URL and everything below it.
auth.check_delay          How long to wait after submitting the form.
auth.check_element        Element to look for to verify login completed.
```
