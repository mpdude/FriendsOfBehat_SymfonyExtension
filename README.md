# Symfony Extension

Integrates Behat with Symfony (`^3.4` and `^4.1`).
 
Inspired by [Behat/Symfony2Extension](https://github.com/Behat/Symfony2Extension).

## Differences

 -  Built-in `symfony` driver uses different kernel than the one that is used in the contexts.
This means you can always change it to any other driver without any issues and 
ensures that application behaviour will not be affected by stateful services.

## Usage

1. Install it:

    ```bash
    $ composer require friends-of-behat/symfony-extension --dev
    ```

2. Enable and configure in your Behat configuration:

    ```yaml
    # behat.yml
    default:
        # ...
        extensions:
            FriendsOfBehat\SymfonyExtension: ~
    ```

3. Good luck & have fun!

    
## Configuration

SymfonyExtension provides kind of autoconfiguration feature.
When none explicit configuration is set, we will set for You sane default that will get you running fast.

**Default Symfony 3 configuration**

```
FriendsOfBehat\SymfonyExtension:
    kernel:
        bootstrap: 'app/autoload.php' # you may want to use var/bootstrap.php.cache instead
        path: app/AppKernel.php
        class: 'AppKernel'
        env: test
        debug: true
```

**Default Symfony 4 configuration**

```
FriendsOfBehat\SymfonyExtension:
    # .env.dist file will be used if .env file does not exist
    env_file: .env
    kernel:
        bootstrap: ~
        path: src/Kernel.php
        class: 'App\Kernel'
        env: test # When explicitly set, will override APP_ENV loaded from env_file file
        debug: true  # When explicitly set, will override APP_DEBUG loaded from env_file file
```

Symfony 4 is detected, based on the existence of `src/Kernel.php` file, so if you did not migrate to new Symfony structure yet; you need to set those values yourself.

Of course, you can always change each of those settings.
