```linux
# apt update
# apt -y upgrade
# vim /etc/ssh/sshd_config
	PermitRootLogin no
	PasswordAuthentication yes

# apt -y install zsh
# chsh -s /usr/bin/zsh
# chsh -s /usr/bin/zsh yechen
# git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
# setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
# vim .zpreztorc
	'syntax-highlighting' \
	'autosuggestions' \
	zstyle ':prezto:module:prompt' theme 'pure'
# source ~/.zpreztorc

# echo "OvO" > /etc/hostname
# reboot
```

