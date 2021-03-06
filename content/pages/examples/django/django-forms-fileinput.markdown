title: django.forms FileInput Example Code
category: page
slug: django-forms-fileinput-examples
sortorder: 500011265
toc: False
sidebartitle: django.forms FileInput
meta: Python example code for the FileInput class from the django.forms module of the Django project.


FileInput is a class within the django.forms module of the Django project.


## Example 1 from dccnsys
[dccnsys](https://github.com/dccnconf/dccnsys) is a conference registration
system built with [Django](/django.html). The code is open source under the
[MIT license](https://github.com/dccnconf/dccnsys/blob/master/LICENSE).

[**dccnsys / wwwdccn / gears / widgets.py**](https://github.com/dccnconf/dccnsys/blob/master/wwwdccn/gears/widgets.py)

```python
# widgets.py
~~from django.forms import FileInput, CheckboxSelectMultiple, Select


~~class CustomFileInput(FileInput):
    template_name = 'gears/widgets/file_input.html'
    accept = ''
    show_file_name = True


class CustomCheckboxSelectMultiple(CheckboxSelectMultiple):
    template_name = 'gears/widgets/checkbox_multiple_select.html'
    hide_label = False
    hide_apply_btn = False

    class Media:
        js = ('gears/js/checkbox_multiple_select.js',)

    def __init__(self, *args, **kwargs):
        self.hide_label = kwargs.pop('hide_label', False)
        self.hide_apply_btn = kwargs.pop('hide_apply_btn', False)
        super().__init__(*args, **kwargs)

    def get_context(self, name, value, attrs):
        context = super().get_context(name, value, attrs)
        context['widget'].update({
            'hide_label': self.hide_label,
            'hide_apply_btn': self.hide_apply_btn,
        })


## ... source file continues with no further FileInput examples...

```

