-------- Pr�sentation de l'exercice activit� 2 du cours "Git & GitHub" 
-------- de Philippe Paill� (ptt.pro@laposte.net)
-------------------------------------------------------------------------------------------
Bonjour,
Cette pr�sentation pour l'activit� 2 du cours "Git & GitHub" arrive � l'occasion d'un travail personnel dont je me sers ici comme support tr�s simplifi� pour la partie correspondant � l'exercice.
	1) tabs: d'abord une utilisation classique de Git pour une partie d�veloppement: mise en conformit� d'une librairie javascript de gestion d'onglets par du code css (WINDEFdemoextrud\Main\Lib\Js\tabs).
	2) utilisation de Git non plus en tant qu'outil mais dans le fonctionnement d'un script syst�me pour l'appel des derni�res librairies ou settings pr�cis�ment lorsque l'on change de configuration utilisateur (ici en cas d'accessibilit� avec une sp�cificit� pour chaque handicap et � un moment de son �volution). Il ne nous �tait pas possible de passer par un bureau virtuel en raison des licences, Git intervient ici en compl�ment d'un shell et d'un script ant qui reconnait et pr�pare le syst�me, on peut choisir une configuration type dans l'historique et dans les branches. De la m�me mani�re, cela est utilisable en d�veloppement pour la conduite de tests en b�n�ficiant d'une organisation clairement structur�e gr�ce au syst�me de branches de Git.
	Bien s�r, l'arborescence ne figure ici qu'� titre d'illustration, le repository lui-m�me se limite � la directory � d�ployer (WINDEFdemoextrud\KleW\Main\Env\Script\Profil). 
	Comme indiqu� dans le cours, les settings et configurations g�r�es concernent l'objet de l'application, les configurations des outils de d�veloppement sont ignor�es.

Deux branches sont ainsi n�cessaires: "devcommon" qui correspond au delivery principal en doublon de "master" par s�curit�. Les fonctionnalit�s compatibles sont d�velopp�es sur la branche "devassistive", je vous pr�sente dans cet exercice un cas simple d'adaptation. L'objectif �tant de s'exercer sur ce que l'on appris.

Les d�veloppeurs sont sur plateforme Windows, nous gardons donc le 'crlf'. Pierre, Jacques travaillent sur le code commun en particulier sur le script lanc� au moment du boot qui est actuellement un simple bat capable entre autres d'individualiser certaines configurations via des variables d'environnement (on ignore pour la pr�sentation les probl�mes de persistance et de gestion des �v�nements qui n�cessitent plut�t des scripts py ou vbs)

Trois �tapes sont effectu�es, une premi�re (tag "devcommon.01") avec configuration de settings g�rant un niveau de debug; pour la pr�sentation un bug intervient, retour via log/blame avant cette �tape sur un commit o� tout marchait bien. Pierre s'aper�oit d'un effet de bord sur la variable du path d'un autre script utile � la configuration, la correction est effectu�e par Jacques qui a d�fini une branche pour les tests.

Sophie travaille sur la mise en conformit� des librairies entre les tags "devassist.00/01" (KleW\Lib\Js\tabs) avec les recommandations en terme d'accessibilit�. En particulier sur l'affichage de pages web avec une taille de fontes devant rester au-dessus d'un certain niveau et le respect de la possibilit� de lancer les pages sans n�cessiter obligatoirement le javascript qui parfois interf�re avec des dispositifs d'aide. Ce d�veloppement peut s'int�grer tout � fait aux librairies communes. Dans notre pr�sentation, il s'agit de deux branches bien distinctes avec une gestion parfaite de la fusion par Git. On reproduit tout de m�me une illustration de la gestion de conflit sur un fichier accessoire (tag "devcommon.02"), la v�rification de la version 2 s'effectue avec "index.html".

=================================================================
tabs
====
No Script - Test de recommandation W3C
branche devassist
Assure la compliance du code de la librairie selon les guidelines d'accessibilit� dans le d�veloppement (W3C Recommendations "Web Content Accessibility Guidelines: 2.3 et 6":
	Checkpoint 3.4, priorit� 2:
		utilisation des unit�s relatives ainsi que 'em' pour les offsets de positionnement
	Checkpoint 2.2, priorit� 2 (images), 1(text):
		codage des couleurs par code num�rique de pr�f�rence au nom g�n�rique en particulier dans le css
	Checkpoints 1.1 et 6.2, priorit� 1:
		Mise en �uvre de l'�l�ment NOSCRIPT
Ce test unitaire d�montre la possibilit� de mettre en �uvre des onglets en utilisant une technique bas�e sur le css de pr�f�rence � l'appel par js.  
----
use:
	indiquer dans votre librairie:
		WINDEFdemoextrud\Main\Lib\Js\tabs
	exemple d'utilisation sous:
		WINDEFdemoextrud\Main\Lib\Js\tabs\index.html
----
Contact:
N'h�sitez pas � me contacter pour des renseignements sur ces guidelines et la norme 5508:
ptt.pro@laposte.net
==================================================================
klew
====
branche devcommon
Utilisation de Git afin de g�rer les sp�cificit�s d'un poste de travail (ex. pr�sence de devices d'accessibilit�, configurations d'IHM ..) appel� lors du boot. Cet utilitaire nous permet d'utilser des applicatifs comme la pr�sentation "tabs" ci-dessus.
use:
Copie de l'arborescence WINDEFdemoextrud sur le disque de d�marrage:
%BOOT_DRIVE%\KleW
Appel lors du d�marrage de Windows du fichier bat:
%BOOT_DRIVE%\KleW\Main\Env\Script\Profil\profilstatic.bat

