This is just an idea. I will implement this in my spare time.

What's problem with cron system of Drupal 7?

- My module have more than one cron job, just one implementation of hook_cron()?
- I wish to have a page /admin/report/cron-jobs, where cron jobs are explained
  very details there.
- My cron job is important, must be run on time. Badly, it is blocked by other!
- I want to see output of the cron job!
- …

Yep, there are many reasons to have an other cron system for your Drupals. This
module try to do that.

To define cron jobs for your module:

````yaml
# %module/config/cron.yml
cron_jobs:
  update_weather:
    controller: \Drupal\my_module\Cron\WeatherCronJob
````

Define your cronjob:

````php
namespace Drupal\my_module\Cron;

use Drupal\at_cron\

class WeatherCronJob implements interface {
}
````

Run the cron job
````bash
# Run all cron jobs in my module
drush at-cron my_module

# Run single job
drush at-cron my_module update_weather
````
