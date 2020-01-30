<!DOCTYPE html>
<html>
<head>
	<title></title>
	<style>
		.top-title {
			text-transform: uppercase;
			font-weight: 700;
			width: 180px;
		    display: inline-block;
		    margin: 10px;
		    position: relative;
		    text-align: center;
		}

		.top-title.active {
			color: red;
		}

		#carousel-custom {
			width: 100%;
		    box-sizing: border-box;
		    overflow: hidden;
		    position: relative;
		}

		#container-titles {
			width: 100%;
		    box-sizing: border-box;
		    overflow: hidden;
		    position: relative;
		}

		.carousel-content {
			width: calc(205px * 8);
			transition: 0.3s;
			left: 0;
		}

		.top-container.active {
			background-color: rgba(0,0,0,0.2);
		}
	</style>
</head>
<body>

	<div id="container-titles">
		<div class="before">BEFORE</div>
		<div class="after">AFTER</div>
		<div class="carousel-content">
			<span class="top-title active" data-toggle="topFiveDevis" data-number="1">Top 5 Devis</span>
	        <span class="top-title" data-toggle="topFiveSujet" data-number="2">Top 5 Sujets</span>
	        <span class="top-title" data-toggle="topFiveFinancementCollectivitesLocales" data-number="3">Top 5 Financement collectivités locales</span>
	        <span class="top-title" data-toggle="topFiveSofica" data-number="4">Top 5 Financement Sofica</span>
	        <span class="top-title" data-toggle="topFiveSalaireRealisateur" data-number="5">Top 5 Salaires Réalisateurs</span>
	        <span class="top-title" data-toggle="topFiveSalaireProducteurs" data-number="6">Top 5 Salaire Producteurs</span>
	        <span class="top-title" data-toggle="topFiveFinancementChainesGratuites" data-number="7">Top 5 Financement Chaines Gratuites</span>
	        <span class="top-title" data-toggle="topFiveFinancementChainesPayantes" data-number="8">Top 5 Financement Chaînes Payantes</span>
		</div>
	</div>

	<hr>

	<div id="carousel-custom">
		<div class="top-container" id="topFiveDevis">
	        <div class="top-content">
	            <h2>Contenu Top 5 Devis</h2>
	        </div>
	    </div>
	    <div class="top-container" id="topFiveSujet">
	        <div class="top-content">
	            <h2>Contenu Top 5 Sujets</h2>
	        </div>
	    </div>
	    <div class="top-container" id="topFiveFinancementCollectivitesLocales">
	        <div class="top-content">
	            <h2>Contenu Top 5 Financement collectivités locales</h2>
	        </div>
	    </div>
	    <div class="top-container" id="topFiveSofica">
	        <div class="top-content">
	            <h2>Contenu Top 5 Financement Sofica</h2>
	        </div>
	    </div>
	    <div class="top-container" id="topFiveSalaireRealisateur">
	        <div class="top-content">
	            <h2>Contenu Top 5 Salaires Réalisateurs</h2>
	        </div>
	    </div>
	    <div class="top-container" id="topFiveSalaireProducteurs">
	        <div class="top-content">
	            <h2>Contenu Top 5 Salaire Producteurs</h2>
	        </div>
	    </div>
	    <div class="top-container" id="topFiveFinancementChainesGratuites">
	        <div class="top-content">
	            <h2>Contenu Top 5 Financement Chaines Gratuites</h2>
	        </div>
	    </div>
	    <div class="top-container" id="topFiveFinancementChainesPayantes">
	        <div class="top-content">
	            <h2>Contenu Top 5 Financement Chaînes Payantes</h2>
	        </div>
	    </div>
	</div>
	<script
	  src="https://code.jquery.com/jquery-3.4.1.min.js"
	  integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo="
	  crossorigin="anonymous"></script>
	 <script>

 	 	let containerSize = $('#container-titles').width();
        console.log(containerSize);

        let carouselSize = $('.carousel-content').width();
        console.log(carouselSize);

        let offsetCarousel = 0;
        let offset = true;

	 	$('.top-title').on('click', function () {
            let associatedContentId = $(this).attr('data-toggle');
            let itemLeftOffset = ($(this).attr('data-number')-1)*204;
            console.dir(itemLeftOffset);
            offsetCarousel = -itemLeftOffset+204;
            $('#container-titles .carousel-content').offset({ left: itemLeftOffset*(-1) + (containerSize/2) - 102 });

            if(!$(this).hasClass('active')) {
                $('.top-container').each(function () {
                    $(this).removeClass('active');
                });
                $('.top-title').each(function () {
                    $(this).removeClass('active');
                });
            }

            $('#' + associatedContentId).addClass('active');
            $(this).addClass('active');
        });


        $('#container-titles .after').on('click', function() {
        	console.log(offsetCarousel);
        	if((containerSize - offsetCarousel + 204) < carouselSize) {
    			offsetCarousel -= 204;
    			$('#container-titles .carousel-content').offset({ left: offsetCarousel });
        	
        	} else {
        		if(offset) {
        			offsetCarousel -= 204;
        			$('#container-titles .carousel-content').offset({ left: offsetCarousel });
        			offset = false;
        		}
        	}
        });
        $('#container-titles .before').on('click', function() {
        	console.log(offsetCarousel);
        	if((offsetCarousel + 204) <= 0) {
				offsetCarousel += 204;
				offset = true;
	        	$('#container-titles .carousel-content').offset({ left: offsetCarousel });
        	} else {
        		// set to offset 0
        	}
        });
	 </script>
</body>
</html>
