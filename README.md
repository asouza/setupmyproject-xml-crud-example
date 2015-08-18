# Here we have some examples about how to create your custom crud

This is the very first version of the crud feature in SetupMyProject. The main goal here is to provide some examples of the xml needed to generate your crud. All tags are specified in the <a href="http://www.setupmyproject.com/crud/crudModels.xsd" target="_blank">xsd file</a>.

## Simple entity

You do not need specify the **id** attribute, it will be generated automatically. Note that, for each Java type that is needed, it is mandatory to specify the fully qualified name of it.

```
<models>
	<model name="Product">
		<field name='name' type='java.lang.String'/>
		<field name='description' type='java.lang.String' />		
		<field name='price' type='java.math.BigDecimal' />		
	</model>
</models>
```

## Related entities

You can create related classes. It is important to notice that you must specify that the **Category** is not a Java type. Another important thing is that you do not need to specify the fully qualified name of **Category** class. It will be assumed that this class should be created in the **models** package of your application. Just to remember, the value of the **type** attribute, for related classes, should be the same used in **name** attribute in related **model** tag.

```
<models>
	<model name="Product">
		<field name='name' type='java.lang.String'/>
		<field name='description' type='java.lang.String' />
		<field name='price' type='java.math.BigDecimal' />
		<field name='category' type='Category' javaType='false'/>
	</model>
	<model name="Category">
		<field name='name' type='String' required='true' />
		<field name='description' type='String' />
	</model>
</models>
```

## Change the html element that will be generated in your view

You will probably want to use a **select** tag to choose the Category of the product. Use the **formInputType** attribute and define your tag type. Another important thing is the **selectLabelField**. You should use it to specify the property name that will be used in the label of your **select**.

```
<models>
	<model name="Product">
		<field name='name' type='java.lang.String'/>
		<field name='description' type='java.lang.String' />
		<field name='price' type='java.math.BigDecimal' />
		<field name='category' type='Category' javaType='false' formInputType='select' formInputName='author.id' selectLabelField="name"/>
	</model>
	<model name="Category">
		<field name='name' type='String'/>
		<field name='description' type='String' />
	</model>
</models>
```

##Try this new feature!

Help us, try to generate some cruds :). We have some great ideas to evolve this feature and SetupMyProject itself, in order to be more present while you are developing your project and not only in the beginning.
