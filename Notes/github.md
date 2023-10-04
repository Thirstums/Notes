# Github things

## Helpful commands for problems

### Remove password promt with every push/pull

```powershell
git config core.sshCommand (get-command ssh).Source.Replace('\','/')
```
