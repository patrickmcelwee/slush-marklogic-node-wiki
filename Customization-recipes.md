# Customization Recipes

Recipes on this page:

- [Add a facet](#add-a-facet)

## Add a facet

To add a facet to the default search page, you will need to create a range
index and a search constraint. Once you do that, the out-of-the-box application
will display a facet for that constraint on the search page. (This is done
using the ml-facets directive that is part of the
[ml-search-ng](https://github.com/joemfb/ml-search-ng) library.)

### Step One to add a facet: Create a range index

Range indexes are added to deploy/ml-config.xml. There are comments there with
examples of several kinds of range indexes. You should be able to uncomment one

For example, to add a range element index on `<name>`, add this inside `<database>` and `<range-element-indexes>` elements:

```xml
<range-element-index>
  <scalar-type>string</scalar-type>
  <namespace-uri/>
  <localname>name</localname>
  <collation>http://marklogic.com/collation/codepoint</collation>
  <range-value-positions>false</range-value-positions>
</range-element-index>
```

Then run this to add the index to the server:

    ./ml local bootstrap

### Step Two to add a facet: Create a search constraint

When searching in MarkLogic, [query
options](https://docs.marklogic.com/guide/search-dev/query-options) can be
saved on the server and invoked during the search.
[Constraints](https://docs.marklogic.com/guide/search-dev/query-options#id_95820)
are one type of option.

The out-of-the-box options file is found in `rest-api/config/options/all.xml`.
(Note that, as you expand your app, you can add other search options
configurations and use them in certain searches.)

To add the search constraint we need, add this inside the `<search:options>`
element:

```xml
<search:constraint name="Name">
  <search:range type="xs:string" facet="true" collation="http://marklogic.com/collation/codepoint">
    <search:facet-option>limit=5</search:facet-option>
    <search:facet-option>frequency-order</search:facet-option>
    <search:facet-option>descending</search:facet-option>
    <search:element ns="" name="name"/>
  </search:range>
</search:constraint>
```

Then run this to deploy those updated options to the MarkLogic server:

    ./ml local deploy rest

If the index and option are configured correctly, and are populated with some
data, you should see the 'Name' facet on the search page.
