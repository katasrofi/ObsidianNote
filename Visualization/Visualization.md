# SVG Fundamental
<html-preview>
	<head>
		<title>Visualization</title>
		<style>
			body {
				margin: 0;
				overflow: hidden;
			}
			text {
				font-size: 100px;
			}
		</style>
	</head>
	<body>
		<svg width = '960' height = '500'>
			<rect
			x = '2'
			y = '3'
			width = '300'
			height = '200'
			fill = 'red'
			stroke = 'blue'
			stroke-width = '2'
			></rect>
			<circle cx='150' cy = '100' r='50'></circle>
			<circle cx='150' cy = '100' r='30' fill = 'blue'></circle>
			<rect
			x = '1'
			y = '2'
			width = '600'
			height = '400'
			fill = 'none'
			stroke = 'blue'
			stroke-width = '2'
			></rect>
			<line
			x1 = '0'
			y1 = '0'
			x2 = '100'
			y2 = '100'
			stroke = 'white'
			stroke-width = '7'
			></line>
			<line
			x1 = '300'
			y1 = '200'
			x2 = '100'
			y2 = '100'
			stroke = 'white'
			stroke-width = '7'
			></line>
			<text x = '400' y = '300' fill = 'white'>Experimental</text>
		</svg>
	</body>
</html-preview>
# Graph
# Javascript
<html-preview>
	<head>
		<title>Visualization</title>
		<style>
			body {
				margin: 0;
				overflow: hidden;
			}
			text {
				font-size: 100px;
			}
		</style>
	</head>
	<body>
		<script>
    		const width = window.innerWidth;
    		const height = window.innerHeight;
    		const svg = document.createElementNS(
        		'http://www.w3.org/svg',
        		'svg'
        	);
    		svg.setAttribute('width', width);
    		svg.setAttribute('height', height);
    		document.body.appendChild(svg);
    		
    		const rect = document.createElementNS(
        		'http://www.w3.org/svg',
        		'rect'
    		);
    		rect.setAttribute('x', 10);
    		rect.setAttribute('width', 10);
    		rect.setAttribute('height', height);
    		svg.appendChild(rect);
    		
    		const n = 100
    		for(let i = 0; i < n; i++){
        		const rect = document.createElementNS(
            		'http://www.w3.org/svg',
            		'rect'
        		);
        		rect.setAttribute('x', i * 20);
        		rect.setAttribute('width', 10);
        		rect.setAttribute('height', height);
        		rect.setAttribute('fill', 'white');
        		svg.appendChild(rect);    		
    		}
    	</script>
	</body>
</html-preview>
# Note
- Lapisan CSS akan diperhatikan lebih dulu dari atribut html, sehingga overlapping dan css berada di bagian paling atas
