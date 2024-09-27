# Matériel de cours sur le Big Data

Bienvenue dans le dépôt du matériel de cours sur le Big Data ! Ce dépôt contient toutes les ressources dont vous aurez besoin pour notre cours de 36 heures réparti sur 12 semaines.

## Structure du dépôt

- `/docs` : Supports de cours en Markdown (les supports seront rajoutés à l'issue de chaque cours)
- `/exercices` : Exercices pratiques (ou TPs) et leurs solutions
- `/ressources` : Matériels de lecture supplémentaires et références
- `/guide-installation` : Instructions d'installation pour les logiciels requis

## Pour commencer

1. Clonez ce dépôt sur votre machine locale :
   ```
   git clone https://github.com/votre-org/materiel-cours-big-data.git
   ```

2. Suivez les instructions d'installation dans le répertoire `/guide-installation` pour votre système d'exploitation.

3. Consultez le programme du cours pour comprendre les sujets que nous aborderons.

## Structure hebdomadaire

Chaque semaine, nous aborderons de nouveaux sujets et effectuerons des exercices connexes. La structure générale est la suivante :

1. Révision du matériel de cours
2. Réalisation des exercices assignés
3. Participation aux discussions et sessions de questions-réponses

## Soumission des exercices

Soumettez vos exercices complétés en les poussant vers votre fork personnel de ce dépôt et en créant une pull request.

## Logiciels requis

- Python 3.8+
- VSCode
- Docker
- Java 1.8
- Hadoop 3.3.6
- Apache Spark 3.5.0

Des instructions d'installation détaillées sont disponibles dans le répertoire `/guide-installation`.

## Ressources supplémentaires

- [Documentation Apache Spark](https://spark.apache.org/docs/latest/)
- [Documentation Hadoop](https://hadoop.apache.org/docs/current/)
- [Designing Data-Intensive Applications](https://dataintensive.net/) par Martin Kleppmann

## Obtenir de l'aide

Si vous rencontrez des problèmes ou avez des questions :

1. Consultez la section FAQ de ce README
2. Contactez l'instructeur (J. Ndetcho) pendant les heures de permanence ou par email: jndetcho@omnesintervenant.com

## FAQ
#### 1. Problèmes d'installation Docker: 
- Unexpected WSL Error:
> Essayer de mettre à jour WSL (Windows Subsystem for Linux), en téléchargeant via le lien suivant: https://github.com/microsoft/WSL/releases
(questions fréquemment posées ici au fur et à mesure qu'elles se présentent pendant le cours)
- Make sure to enable Hyper-V:
```
bcdedit /set hypervisorlaunchtype auto
shutdown /r /t 0
```
- S'assurer que l'option CPU-SVM du BIOS est activée
```bash
systeminfo
```
ou
```powershell
(Get-CimInstance -ClassName Win32_Processor).VMMonitorModeExtensions
``` 
- Si l'erreur persiste, essayez de réinstaller Docker, en décommentant 'recommended WSL' lors de la réinstallation.

## Licence

Ce matériel de cours est sous licence Creative Commons.

---

Bon apprentissage !
