#### Les raccourcis Illustrator pour la disposition sont "cassés" depuis la CS5

(impossible d'attribuer les raccourcis historiques `ctr+(` ou `ctrl+shift+(` par ex). Voilà l'astuce pour que tout fonctionne en attendant un correctif.

Enregistrez un nouveau jeu de raccourcis personnalisés, puis fermez illustrator.

Cherchez votre jeu de raccourci (.kys) dans le dossier de préférence illustrator dans votre dossier utilisateur

- Windows 7/8/10 : `C:\Users\Windows\AppData\Roaming\Adobe\AdobeIllustratorVersion\fr_FR\mycustomshortcut.kys` (ou touche windows+r, taper %APPDATA% puis entrée pour accéder direct au dossier roaming)
- Windows XP : `\Document and Settings\<user name>\Application Data\Adobe\Adobe\Illustrator CS5 Settings\fr_FR\mycustomshortcut.kys`
- Mac : `user/Library/Preferences/Illustrator CS5 Settings/[language]/mycustomshortcut.kys`

#### Cherchez les lignes :

    /sendToBack {
    	/Context 0
    	/Modifiers 96
    	/Represent 40
    	/Key 57
    }
    /sendBackward {
    	/Context 0
    	/Modifiers 224
    	/Represent 81
    	/Key 81
    }
    /sendForward {
    	/Context 0
    	/Modifiers 96
    	/Represent 43
    	/Key 61
    }
    /sendToFront {
    	/Context 0
    	/Modifiers 96
    	/Represent 25
    	/Key 25
    }

#### Remplacez-les par :

    /sendToBack {
    	/Context 0
    	/Modifiers 96
    	/Represent 40
    	/Key 40
    }
    /sendBackward {
    	/Context 0
    	/Modifiers 64
    	/Represent 40
    	/Key 40
    }
    /sendForward {
    	/Context 0
    	/Modifiers 64
    	/Represent 41
    	/Key 91
      }
    /sendToFront {
    	/Context 0
    	/Modifiers 96
    	/Represent 41
    	/Key 91
    }

**Sur Mac, utilisez 91 au lieu de 41 comme valeur de "represent" pour sendForward et sendToFront**
