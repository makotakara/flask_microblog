# GIT
# Install
sudo apt-get install git
# config
git config --global user.name "makotakara"
git config --global user.email romanbog@gmail.com
git config --global color.ui true
git config --global color.status auto
git config --global color.branch auto
# create new repository
mkdir flask_microblog 
cd flask_microblog
git init
git add .
vi GIT.md
git commit -m 'New file GIT.md'
git branch -M main
git remote add origin git@github.com:makotakara/flask_microblog.git
git push -u origin main

# Сделал изменения, сохранил, сделал коммит
git commit -m 'comment'
# Запушил в remote repository
git push -u origin main