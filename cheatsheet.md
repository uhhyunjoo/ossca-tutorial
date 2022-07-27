# shell

- Ref : https://devblog.pytorchlightning.ai/quick-contribution-guide-86d977171b3a

```
git log --oneline

git config --global user.email "alro923@naver.com"
git config --global user.name "Hyunjoo Lee"
git config --global core.editor vim

```

```
git clone git@github.com:alro923/lightning.git

pip install torch==1.11.0 torchvision==0.12.0 torchaudio==0.11.0

pip install . #setup.py 확인

cd lightning/

git remote add upstream git@github.com:Lightning-AI/lightning.git

git remote -v

git fetch --all --prune

git checkout -b tests/13445-mnist_datamodule
```

```
python -m pytest mnist_datamodule.py
```




