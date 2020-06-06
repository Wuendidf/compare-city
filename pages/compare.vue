<template>
  <div class="compare">
    <div class="container">
      <div class="text-center">
        <h3 class="section-heading text-uppercase">Compare cost of living between cities:</h3>

        <div class="form-group">
          <input class="first-city" type="text" value required="required" placeholder="first-city" />
          <h2>VS</h2>
          <input
            class="second-city"
            type="text"
            value
            required="required"
            placeholder="second-city"
          />
        </div>
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Compare</button>

        <div class="row">
          <div class="col-lg-6 col-sm-8 mb-6">
            <div class="portfolio-item">
              <a class="portfolio-link" data-toggle="modal" href="#portfolioModal1">
                <div class="portfolio-hover">
                  <div class="portfolio-hover-content">
                    <i class="fas fa-plus fa-3x"></i>
                  </div>
                </div>
                <img class="img-fluid" src="assets/img/portfolio/01-thumbnail.jpg" alt />
              </a>
              <div class="portfolio-caption">
                <div class="portfolio-caption-heading">Sevilla</div>
                <div class="portfolio-caption-subheading text-muted">first-City</div>
              </div>
            </div>
          </div>

          <div class="col-lg-6 col-sm-8 mb-6">
            <div class="portfolio-item">
              <a class="portfolio-link" data-toggle="modal" href="#portfolioModal1">
                <div class="portfolio-hover">
                  <div class="portfolio-hover-content">
                    <i class="fas fa-plus fa-3x"></i>
                  </div>
                </div>
                <img class="img-fluid" src="assets/img/portfolio/01-thumbnail.jpg" alt />
              </a>
              <div class="portfolio-caption">
                <div class="portfolio-caption-heading">Sevilla</div>
                <div class="portfolio-caption-subheading text-muted">Second City</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

