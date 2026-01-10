## Pricing

<table  class="table table-hover">
  <thead>
    <tr>
      <th>Alteration Type</th>
	  <th></th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    {% for item in site.data.pricing.alterations_pricing.services %}
      <tr>
        <td>{{ item.service }}</td>
        <td>{{ item.description | markdownify }}</td>
        <td>{{ item.price }}</td>
      </tr>
    {% endfor %}
  </tbody>
</table>
*Note: Prices may vary based on the complexity and material of the garment. Please contact us for a detailed quote.*