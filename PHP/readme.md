# PHP Environment Configuration

First, kill off Apache installed by default. Why? TLDR: Default apache sucks and doesn't work with older versions of PHP.

You can test to see if it's already running by running the following command in terminal: `sudo lsof -i:80`

If the system default apache is running you will receive some output, otherwise nothing will output.

If the default apache is running, run the following command: `sudo launchctl unload -w /System/Library/LaunchDaemons/org.apache.httpd.plist`

This will stop the default apache from starting. Death to default. Yay!

## Time to Brew

We'll be installing a few packages via Homebrew
- httpd (Apache)
- nginx
- php (Currently maintained PHP versions)
- shivammathur/php (Legacy PHP 5-7.4.x)
- dnsmasq (for pretty URLs)

Run the following:

- `brew doctor`
- `brew update`
- `brew install httpd`
- `brew install nginx`
- `brew install php`
- `brew tap shivammathur/php`
- `brew install dnsmasq`

## Configuring Apache

## Configuring Nginx

## Using PHP versions
Because Homebrew isn't keepind deprecated versions of PHP around, that'w what we're relying on [Shivamathur PHP](https://github.com/shivammathur/homebrew-php) for. PHP 5.6-Current (8.1 stable, 8.2 beta as of writing)

Install each individual version by the following:

`brew install shivammathur/php/php@<version.number>`

e.g. `brew install shivammathur/php/php@7.1`

### Switching between PHP versions
After PHP versions have been installed, to switch between them, simply run the following command:

`brew link --overwrite --force shivammathur/php/php@<version.number>`

e.g. `brew link --overwrite --force shivammathur/php/php@7.1`

Once you have ran that command, verify the PHP version in your shell by running: `php -v`

You should see the version you have specified output in your shell.

#### Restart the webserver
After any PHP or Apache or Nginx changes, run the following command in your shell: `brew services restart httpd` or `brew services restart nginx`

## Configuring DNSMASQ

## Installing and Configuring Composer
