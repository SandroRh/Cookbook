## Passos
1. Criar arquivo .desktop
2. Inserir as informações necessárias
3. Exemplo de arquivo .desktop (que foi customizado por mim)
```linux
[Desktop Entry]
Version=5.0.4
Name=JetBrains PhpStorm
# Only KDE 4 seems to use GenericName, so we reuse the KDE strings.
# From Ubuntu's language-pack-kde-XX-base packages, version 9.04-20090413.
GenericName=Text Editor

Exec=/opt/phpstorm/bin/phpstorm.sh
Terminal=false
Icon=/opt/phpstorm/bin/phpstorm.png
Type=Application
Categories=TextEditor;IDE;Development
X-Ayatana-Desktop-Shortcuts=NewWindow

[NewWindow Shortcut Group]
Name=New Window
Exec=phpstorm
TargetEnvironment=Unity
```