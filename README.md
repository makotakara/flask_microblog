# GIT install
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
vi README.md
git commit -m 'New file README.md'
git branch -M main

##################################
# Добавление ssh ключа в github
# Генерация нового ключа
ssh-keygen -t ed25519 -C "romanbog@gmail.com"
# Запуск ssh агента
eval "$(ssh-agent -s)"
# Добавьте свой закрытый ключ SSH в ssh-agent.
ssh-add ~/.ssh/id_ed25519
# Добавить ключ в свою УЗ
cat ~/.ssh/id_ed25519.pub
# Settings -> SSH and GPG keys -> New SSH key
https://github.com/settings/keys
# Test connections
ssh -T git@github.com

##################################
# Добавить новый remote repository
git remote add origin git@github.com:makotakara/flask_microblog.git

# Появился новый файл, добавь его в гит
git add .
# Сделал изменения, сохранил, сделал коммит
git commit -a -m 'comment'
# Запушил в remote repository
git push -u origin main

##################################
# Начало работы на новом сервере
# Установить GIT, добавить ssh ключи для github
# Открыть порт в файерволле
sudo ufw allow 5000

# Склонировать репозиторий
cd project/
git clone git@github.com:makotakara/flask_microblog.git
cd flask_microblog

# Если репозиторий уже склонирован и нужно получить изменения в репозитории
cd project/flask_microblog/
git pull origin main
cd flask_microblog

# Создать вирт. среду (Для 1-го раза)
python3 -m venv venv
# Активировать вирт. среду
source venv/bin/activate
## Деактивировать вирт. среду
deactivate

## Записать версии пакетов в requirements.txt
pip freeze > requirements.txt
## Установить пакеты из requirements.txt 
pip install -r requirements.txt

# Запуск приложения на localhost
flask run
# Запуск приложения на внешнем ip
flask run --host=0.0.0.0