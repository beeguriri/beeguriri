### β£Github μ¬μ©λ²
<br>

π κ³΅ν΅

```bash
git config --global user.name "[user name]"
git config --global user.email "[user email]"
```

- [x] email μ€νλλ©΄ μλ μμ¬μ΄μ§λ μ μνμ!!!

```bash
git pull origin main	//pushνκΈ°μ μ λ°λμ pull λ¨Όμ  ν΄μ£ΌκΈ°!

git add .
git commit -m "[commit message]"
git push origin main
```
<br>


π ν΄λ μλ μμ± (clone)

- githubμμ repository μμ±

```bash
git clone [repository url]
```
<br>


π μμ±λμ΄μλ ν΄λμ μ°κ²°

- readme νμΌ μ°μ  μμ±νμ§ λ§κ³  μ§ν

```bash
git init
git remote add origin ["repository url"]
git branch -M main
git push -u origin main
```
<br>


π git igonreνμΌ μμ±

- μ°Έμ‘°μ¬μ΄νΈ : https://www.toptal.com/developers/gitignore

- μμ±λ² (.gitignore)

```bash
# νΉμ  νμΌ λ¬΄μ
νμΌλͺ.νμ₯μ

# ν΄λΉ νμ₯μ νμΌ μ μ²΄ λ¬΄μ
*.νμ₯μ

# ν΄λΉ ν΄λμμ νμΌ μ λΆ λ¬΄μ
ν΄λλͺ/

# ν΄λΉ ν΄λμμ ν΄λΉ νμ₯μ νμΌ μ λΆ λ¬΄μ
ν΄λλͺ/*.νμ₯μ

# ν΄λΉ ν΄λ ν¬ν¨ νμ λͺ¨λ  ν΄λμ ν΄λΉ νμ₯μ νμΌ μ λΆ λ¬΄μ
ν΄λλͺ/**/*.νμ₯μ

# νμ  ν΄λμ ν΄λΉ νμ₯μ νμΌ μ λΆ λ¬΄μ
/*.νμ₯μ
```

- git CMDμμ κΈ°μ‘΄ commit κΈ°λ‘ μ­μ 

```bash
git rm -r --cached .
git add .
git commit -m "Apply .gitignore"
git push origin main
```
