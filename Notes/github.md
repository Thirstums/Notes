# Github things

## Helpful commands for problems

### Disable sslverification

```powershell
 git -c http.sslVerify=false clone [your githublink]
```


### Remove password promt with every push/pull

```powershell
git config core.sshCommand (get-command ssh).Source.Replace('\','/')
```
