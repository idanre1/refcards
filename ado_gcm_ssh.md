GPG with ADO on linux
===
How to correctly setup GPG to handle gcm auth on ADO
# install
```bash
dotnet tool install -g git-credential-manager
sudo apt install gpg pass
```
# ~/.gitconfig
```config
[credential]
	azreposCredentialType = pat
	credentialStore = gpg
	msauthFlow = devicecode
	trace = ~/tmp/git.log
```
# debug gcm
export GIT_TRACE=~/tmp/git.log; GCM_TRACE=~/tmp/git.log;
# references
- https://github.com/git-ecosystem/git-credential-manager/blob/main/docs/credstores.md#gpgpass-compatible-files
- https://techoverflow.net/2021/09/19/how-to-fix-git-credential-manager-core-git-fatal-no-credential-backing-store-has-been-selected/
- https://superuser.com/questions/520980/how-to-force-gpg-to-use-console-mode-pinentry-to-prompt-for-passwords
