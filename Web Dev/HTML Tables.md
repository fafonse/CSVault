
HTML tables are useful for grouping up information together, but it doesn't display itself any differently by default.

## Tags/Parts

`<table>` - The main tag that contains everything within the table
`<thead>` - Container tag for the head/info section of the table
- Set this up for accessibility (screen readers)
`<tr>` - A single table row, for constructing the table head
`<th>` - Within a `<tr>`, and constructs the individual columns for the `<thead>`
`tbody` - Container tag for all the data entries
`<td>` - A table data entry, contained within a `<tr>`
`<tfoot>` - Container tag for table footer



### Code Example

```html
<table>
	<thead>
		<tr> // single row
			<th>Category</th>
			<th>$$$</th>
			<th>Rating</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Chocolate</td>
			<td>Peanut Butter</td>
		</tr>
	</tbody>
	<tfoot>
	</tfoot>
</table>
```


## CSS
Selecting an item/type requires selecting it within the table itself, otherwise it don't work.

```CSS
table {border: 2px solid black;}
table th {border: 1px solid black;}
```

### Combining Borders
`border-collapse: collapse` - Requires that the table and the table data entries have individual borders.

### Spanning Rows
Inside the `<td>` you can set that one data entry to span several rows downward with rowspan.
`<td rowspan="3">lorem ipsum</td>`

### Selecting rows
`tr:nth-child(n)` - Sets the *nth child* CSS of the table row.  Can specify $n$ to *even* or *odd* to color every other row.
`