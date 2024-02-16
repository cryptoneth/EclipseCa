یه سرور حد اقلی لازمه اگر هم برای
پروژه هایی مثل اوایل سرور دارد هموجا ران کنید


پیش نیاز ها

sudo apt -qy update

sudo apt -qy upgrade

sudo apt -qy install curl
sudo apt -qy install git

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash

ترمینال رو کامل ببند مجدد باز کن


-----------------------------------------------------

nvm install –lts

node –version

چک کن ورژن بالای 20 باشه

npm install -g yarn




سولانا رو نصب میکنیم CLI

sh -c "$(curl -sSfL https://release.solana.com/stable/install)"

صبر کن نصب شه

ترمینال رو کامل ببند مجدد باز کن

-----------------------------------------------------



رو نصب میکنیم Rust and Cargo


curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

عدد 1 رو بزن
صبر کن تموم شه

source "$HOME/.cargo/env"

ترمینال رو ببند دوباره باز کن


-----------------------------------------------------

solana --version
rustc --version
cargo --version

چک کن ورژن هاشونو هر سه باید نصب شده باشه


-----------------------------------------------------

یه کیف ایجاد کن .

solana-keygen new

نکته : قسمت 
BIP39
نمیخواد پسوورد بذاری . فقط اینتر بزن
حالا یه ادرس عمومی بهت میده
و زیرش یک 12 کلمه بهت میده
اون رو یاد داشت کن
یه فایل 
ID.Json 
هم تو مسیری که گفته ساخته خواستی با برنامه 
FileZilla 
به سرورت وصل شو . از اون مسیر از اون فایل هم بک اپ بگیر رو سیستمت ( چیز مهمی نیست )

-----------------------------------------------------

هم میخوایم تستنت هم Devnet  کانتدکت بسازیم کاری که میکنید این هست که الان میریم سراغ تستنت

TESTNET

یه کیف متامسک بساز . اتر سپولیا توش فاست بگیر . از سپولیا از سایتی که میذارم بریج بزن به ادرسی که بالا تر به عنوان Public Address / Key
بهت داد

https://hkey0.github.io/EclipseBridge/

از سایت بالا اتریوم که بریج زدی

یه ربعی صبر کن که پولت برسه به شبکه

حالا کد های زیر رو بزن


solana config set --url https://testnet.dev2.eclipsenetwork.xyz

sudo apt-get install bzip2

solana-test-validator






اگه یه همچین چیزی اومد اوکی هست

##if you see something like Below
##⠐ 00:00:27 | Processed Slot: 63 | Confirmed Slot: 63 | Finalized Slot: 31 | Full Snapshot Slot: - | Incremental Snapshot Slot: - | Transactions: 62 | ◎499.999690000


Crtl + c
بزن خارج شی

کد های زیر رو بزن

mkdir eclipse

cd ~/eclipse

git clone https://github.com/solana-labs/example-helloworld

cd example-helloworld

npm install

npm audit fix

npm audit fix --force


حالا صبر کن تموم شه . ترمینال رو ببند باز کن


مجدد برو تو پوشه با کد زیر

cd ~/eclipse/example-helloworld

کد هارو بزن

sudo apt install build-essential -y

npm run build:program-rust

سر این اخری حتی اگر فضای خالی میبینی و هیچی نیست صبر کن چندین دقیقه تا تموم شه


تموم که شد کد های زیر رو اجرا کنید

solana program deploy dist/program/helloworld.so

npm run start




یه همچین چیزی اگر دیدید تمومه

Let's say hello to a Solana account...
Connection to cluster established: https://testnet.dev2.eclipsenetwork.xyz { 'feature-set': 3073089885, 'solana-core': '1.17.6' }
Using account 3kUzbwbRmUvArWbCDfuXdD84yvjYH8Bn1qvMa4rvabnP containing 0.093504332 SOL to pay for fees
Using program 125BDeJf4J4ZFQwZ8xUFTyuqiDQtF4kLvBrVV13n2upb
Saying hello to HAnTnWc6dPQgoTxRQvacaivbVFi8MhcP6bmUYzCrr5En
HAnTnWc6dPQgoTxRQvacaivbVFi8MhcP6bmUYzCrr5En has been greeted 2 time(s)
Success
root@vmi1653886:~/eclipse/example-helloworld#


حالا دیگه خیلی راحت میریم رو Devnet  هم کانترکت بسازیم چون همه زیر ساخت ها اماده شده




فقط RPC  رو روی Devnet میذاریم

کد پایین رو کامل کپی کنید

solana config set --url https://staging-rpc.dev.eclipsenetwork.xyz


با کد زیر فاست بگیرید

solana airdrop 10

حالا مجدد با کد زیر کانترکت بسازید

solana program deploy dist/program/helloworld.so

حالا اجراش کنید

npm run start


اگر همچین چیزی دیدید تمومه
Let's say hello to a Solana account...
Connection to cluster established: https://staging-rpc.dev.eclipsenetwork.xyz { 'feature-set': 1879391783, 'solana-core': '1.14.19' }
Using account 3kUzbwbRmUvArWbCDfuXdD84yvjYH8Bn1qvMa4rvabnP containing 9.36242976 SOL to pay for fees
Using program 125BDeJf4J4ZFQwZ8xUFTyuqiDQtF4kLvBrVV13n2upb
Creating account HAnTnWc6dPQgoTxRQvacaivbVFi8MhcP6bmUYzCrr5En to say hello to
Saying hello to HAnTnWc6dPQgoTxRQvacaivbVFi8MhcP6bmUYzCrr5En
HAnTnWc6dPQgoTxRQvacaivbVFi8MhcP6bmUYzCrr5En has been greeted 1 time(s)
Success
root@vmi1653886:~/eclipse/example-helloworld#

تنها فرقی که کرد بخش RPC  متن هست


قسمت USING ACCOUNT 
تو خروجی ببینید همون ادرس پابلیکی باشه که اول اول بهتون داد و Seed  رو 
سیو کردید



حالا از یکی از همین خروجی هایی که بهتون میده کد Using Program / Program ID  رو کپی کنید

https://docs.google.com/forms/u/0/d/e/1FAIpQLSfJQCFBKHpiy2HVw9lTjCj7k0BqNKnP6G1cd0YdKhaPLWD-AA/formResponse


فرم بالا رو پر کنید . کد Program  که ازتون میخواد همون کانرکتی هست که دیپلوی کردید و گفتم



تمام
