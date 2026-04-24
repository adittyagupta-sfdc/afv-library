# record_flexipage:dynamicHighlights (RecordPage Header)

**Use for:** Displaying key record information and actions prominently. This component is particularly useful for providing a quick and configurable overview of record details.

**Location:** Must be in `header` region.

**Explicit Fields:** Use the most important fields to show a summary of the record. The single primary field is used to identify the record, like a name. The secondary fields (max 12, recommended 6) are used as a summary of the record.

**Structure:** Requires three flexiPageRegions: one template region (Region type) that contains the component and two facets (one for the primary field and one for the secondary fields) that are referenced by the component.

```xml
<flexiPageRegions>
    <itemInstances>
        <fieldInstance>
            <fieldInstanceProperties>
                <name>uiBehavior</name>
                <value>none</value>
            </fieldInstanceProperties>
            <fieldItem>Record.Name</fieldItem> <!-- or other primary field -->
            <identifier>RecordNamePrimaryField</identifier>
        </fieldInstance>
    </itemInstances>
    <name>Facet-PrimaryFields</name>
    <type>Facet</type>
</flexiPageRegions>
    
<flexiPageRegions>
    <itemInstances>
        <fieldInstance>
            <fieldInstanceProperties>
                <name>uiBehavior</name>
                <value>none</value>
            </fieldInstanceProperties>
            <fieldItem>Record.Phone</fieldItem> <!-- or other secondary field -->
            <identifier>RecordPhoneSecondaryField0</identifier>
        </fieldInstance>
    </itemInstances>
    <!-- additional secondary fields -->
    <itemInstances>
        ...
    </itemInstances>
    
    <name>Facet-SecondaryFields</name>
    <type>Facet</type>
</flexiPageRegions>
<flexiPageRegions>
    <itemInstances>
        <componentInstance>
            <componentInstanceProperties>
                <name>actionNames</name>
                <valueList>
                    <valueListItems>
                        <value>Edit</value>
                    </valueListItems>
                    <valueListItems>
                        <value>Delete</value>
                    </valueListItems>
                </valueList>
            </componentInstanceProperties>
            <componentInstanceProperties>
                <name>numVisibleActions</name>
                <value>3</value>
            </componentInstanceProperties>
            <componentInstanceProperties>
                <name>primaryField</name>
                <value>Facet-PrimaryFields</value> <!-- reference to facet containing primary field -->
            </componentInstanceProperties>
            <componentInstanceProperties>
                <name>secondaryFields</name>
                <value>Facet-SecondaryFields</value> <!-- reference to facet containing secondary fields -->
            </componentInstanceProperties>
            <componentName>record_flexipage:dynamicHighlights</componentName>
            <identifier>record_flexipage_dynamicHighlights</identifier>
        </componentInstance>
    </itemInstances>
    <name>header</name>
    <type>Region</type>
</flexiPageRegions>
```
