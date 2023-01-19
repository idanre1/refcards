# token
Is needed for nbdev_new  
https://github.com/settings/personal-access-tokens
```sh
~/azure_scripts/args_to_aes_file.sh GITHUB_TOKEN=secret_token


source ~/azure_scripts/env_from_aes_file.sh <filename>.aes
echo $GITHUB_TOKEN
```

Now you can create a new nbdev repo
