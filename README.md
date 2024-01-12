# Filament Theme "OS Light"

Are you looking for a theme that feels more like an app? Then the 'OS Light' theme is just right for you, especially when you run it as an webapp (browser without toolbar)! The lighter font enhances readability, less borders give you a smoother feeling.
The colors in the theme are pre-defined, so you simply need to install it via composer, and you can start right away.

## Screenshots

![Screenshots](https://raw.githubusercontent.com/mvenghaus/filament-theme-os-light-docs/main/images/screenshots.gif)

## Requirements

You need Filament v3 and a valid license to use this theme.

## Installation

To install the package via composer you need to add the private repository to your composer.json.

```json

"repositories": [
    {
        "type": "composer",
        "url": "https://filament-theme-os-light.composer.sh"
    }
]

```

Now you are ready to install the package:

```bash
composer require mvenghaus/filament-plugin-theme-os-light:"^3.0"
```

You will be asked for a username and password. Use your order email address as username and the license key you received as password.

### Stylesheets

If you want to use a different design in Filament, you'll need to create a theme first. If you're using the default Filament setup with everything included, you can follow this guide. 
For more information [click here](https://filamentphp.com/docs/3.x/panels/themes#creating-a-custom-theme).

```bash
php artisan make:filament-theme
```

A file is created as follows:

```bash
resources/css/filament/admin/theme.css
```

You just need to edit the CSS file so that it uses the theme file.

```diff
- @import '/vendor/filament/filament/resources/css/theme.css';
+ @import '/vendor/mvenghaus/filament-theme-os-light/resources/css/index.css';
```

Now, you just need to ensure that Tailwind processes the file. You can achieve this by including the path in your vite.config.js.

```diff
- input: ['resources/css/app.css', 'resources/js/app.js'],
+ input: ['resources/css/app.css', 'resources/js/app.js', 'resources/css/filament/admin/theme.css'],
```

Finally, build the CSS file.

```bash
npm run build
```

### Configuration

The plugin needs to be registered and configured.

```php
<?php
 
namespace App\Providers\Filament;
 
use Mvenghaus\FilamentThemeOs\FilamentThemeOsLight;
use Filament\Panel;
use Filament\PanelProvider;
 
class AdminPanelProvider extends PanelProvider
{
    public function panel(Panel $panel): Panel
    {
        return $panel
            ->plugin(
                FilamentThemeOsLight::make()
                    ->withLogoInTopbar() // optional
            )
            ->viteTheme('resources/css/filament/admin/theme.css');
    }
}
```

#### Options

##### withLogoInTopbar
As you can see in the code above, there's an option to move the logo into the top bar. By doing so, you achieve a more compact view, making it even more app-like.

> **NOTE:** If you choose this option, make sure not to use any additional elements in the sidebar navigation header, otherwise they will not be visible.

> **TIPP:** To prevent the logo from flickering during page reload, you should enable livewire:navigate ([read more](https://filamentphp.com/docs/3.x/panels/configuration)).
> ```php
> $panel->spa() 
> ```

# Recommended Settings
To get the most out of it i suggest a few settings:

* maxContentWidth to "Full" ([read more](https://filamentphp.com/docs/2.x/admin/appearance#changing-the-maximum-content-width))
* inline your fields ([read  more](https://filamentphp.com/docs/2.x/forms/fields#checkbox))
* pin it to your system's dock like a native app
  * Linux ([read more](https://github.com/linuxmint/webapp-manager))
  * Mac (no idea)
  * Windows (no idea)

Full featured:





# Contact
If you any questions or you find a bug, please [contact me via email](mailto:support@inklammern.de).