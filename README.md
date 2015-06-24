# iOS Meta Refresh

iOS Mail Application Meta-Refresh King Phisher Template

The original [iOS-Mail.app-inject-kit
](https://github.com/jansoucek/iOS-Mail.app-inject-kit) was written in PHP and used Apache as the web server. This version have been created specifically for use with the Phishing Tool [King Phisher](https://github.com/securestate/king-phisher).

Using Jinja, the displayed iOS password prompt will automatically change depending on the target email domain. Currently there are five different password prompts for gmail.com, yahoo.com, hotmail.com, and icloud.com. Any other email domain not matching these four will be considered a corporate email address connected through Exchange and display the more generic "Enter the password for the Exchange account `{{ client.email_address }}`".

Additionally, once the user has opened the email and submitted their credentials, King Phisher detects the client visit count using the Jinja variable `client.visit_count`. If this visit count is greater than one, `{% if client.visit_count <= 1 %}`, the user will not be shown the password prompt. Instead, they will be immediately shown the email message contents, which is "Important Information: Please Read!".  

## License

This code is released under the MIT license, for more details see
the [LICENSE](https://github.com/coldfusion39/iOS-Meta-Refresh/blob/master/LICENSE) file.

## Credits

Credit should be given to [jansoucek](https://github.com/jansoucek) and his original Proof of Concept [iOS-Mail.app-inject-kit
](https://github.com/jansoucek/iOS-Mail.app-inject-kit).

## Usage

- Import `email.html` into King Phisher as the "Message HTML File".
- Upload the contents of `www` to your King Phisher server and set your "Web Server URL" to `auth`.
- Make sure the King Phisher server is configured to require a message ID `require_id: true` in order capture submitted credentials.
