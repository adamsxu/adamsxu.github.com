---
layout: post
title: "Git Configure"
category:
tags: [git,github]
---
{% include JB/setup %}

1. Console 显示分支以及上次commit之后过了多少时间

	修改~/.bash_profile

		function git_branch {
		  ref=$(git symbolic-ref HEAD 2> /dev/null) || return;
		  echo "("${ref#refs/heads/}") ";
		}
		function git_since_last_commit {
		  now=`date +%s`;
		  last_commit=$(git log --pretty=format:%at -1 2> /dev/null) || return;
		  seconds_since_last_commit=$((now-last_commit));
		  minutes_since_last_commit=$((seconds_since_last_commit/60));
		  hours_since_last_commit=$((minutes_since_last_commit/60));
		  minutes_since_last_commit=$((minutes_since_last_commit%60));
		  echo "${hours_since_last_commit}h${minutes_since_last_commit}m ";
		}
		PS1="[\[\033[1;32m\]\w\[\033[0m\]] \[\033[0m\]\[\033[1;36m\]\$(git_branch)\[\033[0;33m\]\$(git_since_last_commit)\[\033[0m\]$ "

	BTW: 本段代码来自 https://gist.github.com/897951

2. ~/.gitconfig

		[color "branch"]
		  current = yellow reverse
		  local = yellow
		  remote = green
		[color "diff"]
		  meta = yellow bold
		  frag = magenta bold
		  old = red bold
		  new = green bold
		[color "status"]
		  added = yellow
		  changed = green
		  untracked = cyan
		[alias]
		  st = status
		  ci = commit
		  br = branch
		  co = checkout
		  l = log --stat
		  pl = pull
		  ps = push
		  ca = commit -a
		  df = diff
		  dc = diff --cached
		  lg = log -p
		  lol = log --graph --decorate --pretty=oneline --abbrev-commit
		  lola = log --graph --decorate --pretty=oneline --abbrev-commit --all
		  hist = log --graph --pretty=format:'%C(cyan)%h%Creset -%C(red)%d%Creset %s %C(yellow)[%an] %Cgreen(%cr)%Creset' --abbrev-commit --date=relative
		  ls = ls-files
		  # Show files ignored by git:
		  ign = ls-files -o -i --exclude-standard
