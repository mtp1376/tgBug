# The Bug
Admist our researches on (https://github.com/telegramdesktop/tdesktop)[Telegram Desktop application], we found a Session Fixation bug, which could lead to full account hijack, alongside with bypassing two-step verification and logging in without any sessions getting recorded.

# Preface
As you know(?), all login datas in Telegram Desktop application are saved inside the `tdata` folder beside the `Telegram.exe` app, so if anybody copy that folder, an account hijack happens.

# Description
The Session Fixation bug appears on the app because "when a session is closed, the token assigned to it doesn't get revoked or replaced by a new one, but it gets re-used".
So that if you do the following steps, you can demo the bug:
1- Get a copy of Telegram Desktop application.
2- Login using one of your accounts to Telegram.
3- Copy the `tdata` folder (or the whole Telegram folder (just `tdata` matters)) to somewhere else.
4- Kill the session you opened in step 2 on your other device; so that both Telegram folders now are logged out.
5- Use one of those Telegram folder copies to login to another Telegram account.
6- Now if you open the other folder, it will open the same session as the other one.
It IS a bug for sure, and it's (https://www.owasp.org/index.php/Session_fixation)[Session Fixation].
