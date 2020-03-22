drf-yasg-examples
-----------------

Add example value on your swagger documentation!


Requirements
============

1. Python 3.6.1 or higher
2. drf-yasg based code base


Install
=======

With pip
++++++++

.. code-block:: sh

   pip install drf-yasg-examples


With Poetry
+++++++++++

.. code-block:: sh

   poetry add drf-yasg-examples


Configuration
=============

Edit your django config file.

.. code-block:: py

   SWAGGER_SETTINGS = {
       'DEFAULT_AUTO_SCHEMA_CLASS': 'drf_yasg_examples.SwaggerAutoSchema',
   }

Note: If you use ``SwaggerAutoSchema`` class other codes, replace them together


Usage
=====

ChoiceField
+++++++++++

Just write verbose text like this in your models.

.. code-block:: py

   class Product(models.Model):

       CATEGORY = [
           ('F', 'Food'),
           ('L', 'Living Item'),
       ]

       category = models.CharField(
           verbose_name='Category',
           max_length=1,
           choices=CATEGORY,
       )


And ModelSerializer might set this field as ChoiceField, and this package
write down enum k-v list on your documentation automatically.


Others
++++++

Write example value in your serializer class like this.

.. code-block:: py

   class ProductSerializer(serializers.ModelSerializer):

       class Meta:
           model = Product
           fields = '__all__'
           example = {
               'name': 'Apple',
               'amount': 6,
               'price': '10.00',
           }


Then drf-yasg will add example on your docs automatically.


LICENSE
=======

MIT
