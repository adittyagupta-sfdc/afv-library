# flexipage:fieldSection

**Use for:** Displaying fields in columns.

**Structure:** Three-level nesting:
1. Template Region (Region type)
2. Column Facets (Facet type)
3. Field Facets (Facet type)

**Critical:** the `columns` property must match the name of the facet where the columns are defined. It is *not* a number.

**Referenced in component property:**
```xml
<!-- field facet for first column -->
<flexiPageRegions>
   <itemInstances>
      <fieldInstance>
            <fieldInstanceProperties>
               <name>uiBehavior</name>
               <value>required</value>
            </fieldInstanceProperties>
            <fieldItem>Record.Field0</fieldItem>
            <identifier>RecordColumn1Field0</identifier>
      </fieldInstance>
   </itemInstances>
   <itemInstances>
      <fieldInstance>
            <fieldInstanceProperties>
               <name>uiBehavior</name>
               <value>none</value>
            </fieldInstanceProperties>
            <fieldItem>Record.Field1</fieldItem>
            <identifier>RecordColumn1Field1</identifier>
      </fieldInstance>
   </itemInstances>
   <!-- any additional fields in first column -->
   <name>Facet-FieldSection-Column1</name>
   <type>Facet</type>
</flexiPageRegions>
<!-- field facet for second column -->
<flexiPageRegions>
   <itemInstances>
      <fieldInstance>
            <fieldInstanceProperties>
               <name>uiBehavior</name>
               <value>none</value>
            </fieldInstanceProperties>
            <fieldItem>Record.Field2</fieldItem>
            <identifier>RecordColumn2Field0</identifier>
      </fieldInstance>
   </itemInstances>
   <itemInstances>
      <fieldInstance>
            <fieldInstanceProperties>
               <name>uiBehavior</name>
               <value>none</value>
            </fieldInstanceProperties>
            <fieldItem>Record.Type</fieldItem>
            <identifier>RecordColumn2Field1</identifier>
      </fieldInstance>
   </itemInstances>
   <!-- any additional fields in second column -->
   <name>Facet-FieldSection-Column2</name>
   <type>Facet</type>
</flexiPageRegions>
<!-- columns facet -->
<flexiPageRegions>
   <itemInstances>
      <componentInstance>
            <componentInstanceProperties>
               <name>body</name>
               <value>Facet-FieldSection-Column1</value> <!-- matches name of field facet for first column -->
            </componentInstanceProperties>
            <componentName>flexipage:column</componentName>
            <identifier>flexipage_column1</identifier>
      </componentInstance>
   </itemInstances>
   <itemInstances>
      <componentInstance>
            <componentInstanceProperties>
               <name>body</name>
               <value>Facet-FieldSection-Column2</value> <!-- matches name of field facet for second column -->
            </componentInstanceProperties>
            <componentName>flexipage:column</componentName>
            <identifier>flexipage_column2</identifier>
      </componentInstance>
   </itemInstances>
   <name>Facet-FieldSection-Columns</name>
   <type>Facet</type>
</flexiPageRegions>
<!-- template region -->
<flexiPageRegions>
   <itemInstances>
      <componentInstance>
            <componentInstanceProperties>
               <name>columns</name>
               <value>Facet-FieldSection-Columns</value> <!-- matches name of columns facet -->
            </componentInstanceProperties>
            <componentInstanceProperties>
               <name>horizontalAlignment</name>
               <value>false</value>
            </componentInstanceProperties>
            <componentInstanceProperties>
               <name>label</name>
               <value>Information</value>
            </componentInstanceProperties>
            <componentName>flexipage:fieldSection</componentName>
            <identifier>flexipage_fieldSection</identifier>
      </componentInstance>
   </itemInstances>
   <name>main</name>
   <type>Region</type>
</flexiPageRegions>
```
