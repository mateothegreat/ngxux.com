# Setup

## Installing Dependencies

First we need to install the basic required dependencies with:

{% code-tabs %}
{% code-tabs-item title="project root" %}
```bash
$ npm install @ngxux/common     \
              @angular/material \
              @angular/cdk
```
{% endcode-tabs-item %}
{% endcode-tabs %}

We'll load the material theme into our `src/app/style.scss` file using an import:

{% code-tabs %}
{% code-tabs-item title="src/app/style.scss" %}
```css
@import "~@angular/material/prebuilt-themes/indigo-pink.css";
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now you're all set to begin dropping in ngxux module libraries!

