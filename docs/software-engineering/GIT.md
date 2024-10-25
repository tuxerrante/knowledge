  
**Forzare il merge di due repo:**  
cd ../new-project  
git remote add old-project ../old-project  
git fetch old-project  
git checkout \-b feature/merge-old-project  
git merge \-S \--allow-unrelated-histories old-project/master  
\# controlla link con repo remoto  
git remote set-url origin https://\_\_\_\_\_  
git push origin feature/merge-old-project  
git remote rm old-project

**Rimuovere un repo remoto**  
git branch \-a  
git push origin \--delete test

