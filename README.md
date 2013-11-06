1) git config --global user.name "Sergey Denisov"
2) git config --global user.email "sergeant.wssa@gmail.com"
3) cd git
4) git clone https://github.com/hhru/frontik
5) git clone frontik testing
6) cd testing
8) git filter-branch --tag-name-filter cat --prune-empty --subdirectory-filter frontik/testing -- --all
9) git reset --hard
10) git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
11) git reflog expire --expire=now --all
12) git gc --aggressive --prune=now
13) cd ../frontik/
14) git filter-branch --tag-name-filter cat --prune-empty --tree-filter "rm -rf frontik/testing" -- --all
15) git reset --hard
16) git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
17) git reflog expire --expire=now --all
18) git gc --aggressive --prune=now
19) git remote rm origin
20) git remote add origin git@github.com:sergdenisov/frontik.git
21) git push --all origin
22) cd ../testing
23) git remote rm origin
24) git remote add origin git@github.com:sergdenisov/testing.git
25) git push --all origin
