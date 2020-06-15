# Ambiente de Desenvolvimento

- VS Code
- PHP (Xdebug)
- Composer
- Nodejs
- Git
- Cmder

# VS Code Configurações e Extensões

THEME
 - One Dark Pro
 - Material Icons Theme
 
EXTENSIONS
 - PHP Debug - Felix Becker
 - PHP Intelephense - Ben Mewburn
 - PHP Namespace Resolver
 - PHP Getters & Setters - phproberto

 - Auto Close Tag
 - EditorConfig for VS Code
 - Laravel Blade Snippets
 - Laravel Blade (Sintax Highlighting)
 - Laravel Goto View
 - Laravel Snippets

 - Inline Parameters for VSCode
 
 - Git History - Don Jayamanne
 - Git Project Manager - Felipe Caputo

 - HTML CSS Support - ecmel
 - HTML Snippets - Mohamed Abusaid

 - XML Tools - Josh Johnson


SETTINGS.JSON

```json
{
    "terminal.external.windowsExec": "C:\\cmder\\Cmder.exe",
    "terminal.integrated.shell.windows": "C:\\Windows\\System32\\cmd.exe",
    "terminal.integrated.shellArgs.windows": [
        "/k C:\\Cmder\\vendor\\init.bat"
    ],
    "workbench.iconTheme": "material-icon-theme",
    "editor.formatOnSave": true,
    "explorer.confirmDelete": false,
    "workbench.colorTheme": "One Dark Pro",
}
```
 
IMPROVEMENTS FOR LARAVEL PROJECTS:
 - composer require --dev barryvdh/laravel-ide-helper --ignore-platform-reqs
 - set in your app/Providers/AppServiceProvider.php:

	```php
	public function register()
	{
		if ($this->app->environment() !== 'production') {
			$this->app->register(\Barryvdh\LaravelIdeHelper\IdeHelperServiceProvider::class);
		}
		// ...
	}
	```

 - run php artisan clear-compiled
 - set in your composer.json (scripts):
    
	```json
	"scripts": {
	    "post-update-cmd": [
		"Illuminate\\Foundation\\ComposerScripts::postUpdate",
		"@php artisan ide-helper:generate",
		"@php artisan ide-helper:meta"
	    ]
	},
	```
   
 - run composer and laravel commands:
 - composer update --ignore-platform-reqs
 - php artisan vendor:publish --provider="Barryvdh\LaravelIdeHelper\IdeHelperServiceProvider" --tag=config
    
CODE STANDARDS (PADRONIZAÇÃO DE CÓDIGO):
 - composer global require friendsofphp/php-cs-fixer
 - instale a extensão no vs code chamada "php cs fixer" do junstyle
 
 - adicione no settings.json do seu vs code o seguinte conteúdo:
   ```json
   "editor.formatOnSave": true,
   "php-cs-fixer.onsave": true,
   "php-cs-fixer.executablePath": "${extensionPath}/php-cs-fixer.phar",
   "php-cs-fixer.config": "~/.vscode/.php_cs;",
   "editor.wordSeparators": "`~!@#%^&*()-=+[{]}\\|;:'\",.<>/?"
   ```
 
 - crie um arquivo .php_cs no diretório .vscode => touch .vscode\.php_cs
 - dentro do .php_cs, insira o conteúdo desse repositório: https://github.com/icarojobs/phpcsfixer-file
 - salve o arquivo, crie um novo arquivo php sem padrões e na hora de salvar, surpreenda-se!
