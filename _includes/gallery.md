<section class="container my-5 resume-section" id="gallery">
  <h2 class="mb-4">Gallery</h2>
  <div class="row g-3">
	  {% assign gallery_files = site.static_files | where_exp: "file", "file.path contains 'assets/images/gallery'" | sort: "path" | reverse %}
		
		{% for file in gallery_files %}
		  {% if file.extname == ".jpg" or file.extname == ".png" or file.extname == ".jpeg" or file.extname == ".webp" %}
			{% assign path_parts = file.path | split: "/" %}
			{% assign folder_index = path_parts | size | minus: 2 %}

			{% comment %} --- SMART CAPTION LOGIC --- {% endcomment %}
			{% assign words = path_parts[folder_index] | replace: "_", " " | split: " " %}
			{% capture folder_title %}
			{% for word in words %}
			  {% assign w = word | downcase %}
			  {% if w == "and" or w == "the" or w == "of" %}{{ w }}{% else %}{{ w | capitalize }}{% endif %}
			{% endfor %}
			{% endcapture %}

			<div class="col-6 col-md-4 col-lg-3">
				<div class="card border-0 shadow-sm">
				  <a href="#" data-bs-toggle="modal" data-bs-target="#imageModal" onclick="updateModal('{{ file.path | relative_url }}')">
					<img src="{{ file.path | relative_url }}" class="card-img-top gallery-thumb" alt="{{ folder_title | strip }}">
				  </a>
				  <div class="card-body p-2 text-center">
					<small class="text-muted fw-bold">{{ folder_title | strip }}</small>
				  </div>
				</div>
			</div>
		  {% endif %}
		{% endfor %}    
    </div>
</section>

<div class="modal fade" id="imageModal" tabindex="-1" aria-hidden="true">
  <div class="modal-dialog modal-dialog-centered modal-lg">
    <div class="modal-content bg-transparent border-0">
      <div class="modal-body p-0 text-end">
        <button type="button" class="btn-close btn-close-white mb-2" data-bs-dismiss="modal" aria-label="Close"></button>
        <img src="" id="modalImage" class="img-fluid rounded" alt="Zoomed View">
      </div>
    </div>
  </div>
</div>