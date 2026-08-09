---
title: Gallery
summary: ''
type: landing

sections:
  - block: markdown
    content:
      text: |-
        **I enjoy exploring nature, traveling across cultures, and observing how people think, communicate, and make decisions. These experiences continually shape the questions I ask as a researcher.**

        <div class="life-photo-gallery" data-life-gallery>
          <div class="life-photo-stack" aria-label="Photo gallery">
            <button class="life-photo" type="button"><img src="/images/life/alpine-valley.jpg" alt="Mist over a green alpine valley" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/open-water.jpg" alt="Swimmers in clear blue water" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/coastal-sculpture.jpg" alt="A sculpture overlooking the sea" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/sunset.jpg" alt="Sunset over tall grass" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/mont-saint-michel.jpg" alt="Mont Saint-Michel rising through mist" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/mount-fuji.jpg" alt="Mount Fuji framed by cherry blossoms" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/yosemite-half-dome.jpg" alt="Half Dome at sunset in Yosemite" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/mediterranean-city.jpg" alt="A Mediterranean city of colorful buildings" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/pastel-houses.jpg" alt="Sunlit pastel houses and balconies" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/eiffel-tower.jpg" alt="The Eiffel Tower framed by trees" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/alpine-walk.jpg" alt="A walk through an alpine village" loading="lazy"></button>
            <button class="life-photo" type="button"><img src="/images/life/stonehenge.jpg" alt="At Stonehenge on a sunny day" loading="lazy"></button>
          </div>
          <div class="life-lightbox" aria-hidden="true" role="dialog" aria-label="Enlarged photograph">
            <button class="life-lightbox-close" type="button" aria-label="Close enlarged photograph" title="Close">×</button>
            <button class="life-lightbox-previous" type="button" aria-label="View previous photograph" title="Previous photograph">‹</button>
            <img class="life-lightbox-image" src="" alt="">
            <button class="life-lightbox-next" type="button" aria-label="View next photograph" title="Next photograph">›</button>
          </div>
        </div>

        <script>
          document.querySelectorAll('[data-life-gallery]').forEach((gallery) => {
            const lightbox = gallery.querySelector('.life-lightbox');
            const lightboxImage = gallery.querySelector('.life-lightbox-image');
            const closeButton = gallery.querySelector('.life-lightbox-close');
            const previousButton = gallery.querySelector('.life-lightbox-previous');
            const nextButton = gallery.querySelector('.life-lightbox-next');
            const photos = Array.from(gallery.querySelectorAll('.life-photo'));
            let currentPhotoIndex = 0;
            const closeLightbox = () => {
              lightbox.classList.remove('is-open');
              lightbox.setAttribute('aria-hidden', 'true');
              document.body.classList.remove('life-lightbox-open');
            };
            const showPhoto = (index) => {
              currentPhotoIndex = (index + photos.length) % photos.length;
              const image = photos[currentPhotoIndex].querySelector('img');
              lightboxImage.src = image.src;
              lightboxImage.alt = image.alt;
              lightbox.classList.add('is-open');
              lightbox.setAttribute('aria-hidden', 'false');
              document.body.classList.add('life-lightbox-open');
            };

            photos.forEach((photo, index) => {
              photo.addEventListener('click', () => {
                if (!gallery.classList.contains('is-expanded')) {
                  gallery.classList.add('is-expanded');
                  return;
                }
                showPhoto(index);
              });
            });

            closeButton.addEventListener('click', closeLightbox);
            previousButton.addEventListener('click', () => showPhoto(currentPhotoIndex - 1));
            nextButton.addEventListener('click', () => showPhoto(currentPhotoIndex + 1));
            lightboxImage.addEventListener('click', () => showPhoto(currentPhotoIndex + 1));
            lightbox.addEventListener('click', (event) => {
              if (event.target === lightbox) closeLightbox();
            });
            document.addEventListener('keydown', (event) => {
              if (event.key === 'Escape') closeLightbox();
              if (lightbox.classList.contains('is-open') && event.key === 'ArrowRight') {
                showPhoto(currentPhotoIndex + 1);
              }
              if (lightbox.classList.contains('is-open') && event.key === 'ArrowLeft') {
                showPhoto(currentPhotoIndex - 1);
              }
            });
          });
        </script>
    design:
      columns: '1'
---
