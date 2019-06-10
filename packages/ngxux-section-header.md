# ngxux-section-header

![](../.gitbook/assets/image%20%286%29.png)

## Installing

{% code-tabs %}
{% code-tabs-item title="project root" %}
```bash
$ npm install @ngxux/section-header
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Usage

{% code-tabs %}
{% code-tabs-item title="app.component.html" %}
```markup
<ngxux-section-header [buttons]="[
                { key: 'somekey', label: 'some label', color: 'warn' },
                { key: 'somekey', label: 'some label', color: 'primary' }
                ]"
    description="This is a section description. You can change me anytime using a service or attribute."
    title="Some Section Title"></ngxux-section-header>
```
{% endcode-tabs-item %}
{% endcode-tabs %}



