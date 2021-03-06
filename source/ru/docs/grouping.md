---
title: Макеты группировки
extends: _layouts.documentation
section: main
lang: ru
---


## Аккордеон

Аккордеоны полезны, когда вы хотите переключаться между скрытием и отображением большого количества контента:

![Accordion](/assets/img/layouts/accordion.png)

Аккордеоны поддерживают короткий синтаксис через вызов статического метода,
что не требует создания отдельного класса:

```php
use Orchid\Support\Facades\Layout;

public function layout(): array
{
    return [
        Layout::accordion([
            'Personal Information' => [
                Layout::rows([
                    Input::make('user.name')
                        ->type('text')
                        ->required()
                        ->title('Name')
                        ->placeholder('Name'),

                    Input::make('user.email')
                        ->type('email')
                        ->required()
                        ->title('Email')
                        ->placeholder('Email'),
                ]),
            ],
            'Billing Address'      => [
                Layout::rows([
                    Input::make('address')
                        ->type('text')
                        ->required()
                        ->title('Адрес доставки')
                        ->placeholder('Ул. Ленина дом 14 оф.162'),
                ]),
            ],
        ]),
    ];
}
```

Ключи будут использованы в качестве заголовков.

Обратите внимание, что вы можете указывать в качестве значений и строчное имя класса:

```php
public function layout(): array
{
    return [
        Layout::accordion([
            'Personal Information' => PersonalInformationRow::class,
            'Billing Address'      => BillingAddressRow::class,
        ]),
    ];
}
```


## Колонки

Колонки полезны, когда вам необходимо сгруппировать контент.

![Columns](/assets/img/layouts/columns.png)

Колонки поддерживают короткий синтаксис через вызов статического метода,
что не требует создания отдельного класса:

```php
use Orchid\Support\Facades\Layout;

public function layout(): array
{
    return [
        Layout::columns([
           TableExample::class,
           RowExample::class,
        ]),
    ];
}
```

## Раскрывающийся список

```php
public function layout(): array
{
    return [
        Layout::collapse([
            Input::make('name')
                ->type('text')
                ->title('Name Articles')
        ])->label('More'),
    ];
}
```


## Набор фильтров

Для группировки фильтров, их сброса и применения, существует отдельный слой `Selection`, в котором они указываются.

Для создания исполните команду:
```php
php artisan orchid:selection MySelection
```

Пример класса:
```php
namespace App\Orchid\Layouts;

use Orchid\Platform\Filters\Filter;
use Orchid\Press\Http\Filters\CreatedFilter;
use Orchid\Press\Http\Filters\SearchFilter;
use Orchid\Screen\Layouts\Selection;

class MySelection extends Selection
{
    /**
     * @return Filter[]
     */
    public function filters(): array
    {
        return [
          SearchFilter::class,
          CreatedFilter::class
        ];
    }
}
```


## Табы

Табы группируют контент и помогают в навигации. Полезны, когда вы хотите переключаться между скрытием и отображением большого количества контента:

![Tabs](/assets/img/layouts/tabs.png)

Табы поддерживают короткий синтаксис через вызов статического метода,
что не требует создания отдельного класса:

```php
use Orchid\Support\Facades\Layout;

public function layout(): array
{
    return [
        Layout::tabs([
            'Personal Information' => [
                Layout::rows([
                    Input::make('user.name')
                        ->type('text')
                        ->required()
                        ->title('Name')
                        ->placeholder('Name'),

                    Input::make('user.email')
                        ->type('email')
                        ->required()
                        ->title('Email')
                        ->placeholder('Email'),
                ]),
            ],
            'Billing Address'      => [
                Layout::rows([
                    Input::make('address')
                        ->type('text')
                        ->required()
                        ->title('Адрес доставки')
                        ->placeholder('Ул. Ленина дом 14 оф.162'),
                ]),
            ],
        ]),
    ];
}
```

Ключи будут использованы в качестве заголовков.

Обратите внимание, что вы можете указывать в качестве значений и строчное имя класса:

```php
public function layout(): array
{
    return [
        Layout::tabs([
            'Personal Information' => PersonalInformationRow::class,
            'Billing Address'      => BillingAddressRow::class,
        ]),
    ];
}
```
