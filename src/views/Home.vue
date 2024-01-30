<template>
    <header style="width:calc(100% - 4rem);top:0rem;margin:2rem;display:flex;flex-flow:row;gap:2rem;">
        <img src="EOC.svg" style="height:100px;" alt="">
        <div class="info-box" style="border:2px solid black;padding:0.5rem 1rem;display:flex;flex-flow:column;justify-content: center;"><p style="font-size:2rem;font-weight:400;">Professional Structural Engineering
and Consulting Services</p> <p style="display:flex;flex-flow:row; gap:1rem;font-weight:800;"><a href=""><b style="font-weight:800;">CALL US</b></a> | <a href=""><b  style="font-weight:800;">EMAIL US</b></a></p></div>
        <div class="info-box" style="border:1px solid black;padding:1rem;display:flex;"><p style="font-weight:400;"></p></div>
     
    </header>
    <div class="bg" style="display:flex;flex-flow:row;justify-content: space-between;padding:2rem;">
        <div class="main-content" style="width:100%;height:calc(100vh - 15rem);background-image:url(octopo.jpg);background-position: center;filter:saturate(0)brightness(1.8)contrast(1);box-shadow:inset 0px 0px 200px white;"></div>
        <div class="sidebar" style="height:calc(100vh - 14rem);margin-top:-10rem;border:4px solid black;width:100px; ">

            <div class="row-to-column" style="border-top:4px solid black;width:fit-content;display:flex;flex-flow:row;left:30px;gap:1rem;transform-origin: bottom left;transform:rotate(90deg);">
                <div><h3>HOME</h3></div>
                <div><h3>ABOUT</h3></div>
                <div><h3>SERVICES</h3></div>
                <div><h3>CONTACT</h3></div>
                <div><h3>NEWS</h3></div>
            </div>
            <hr style="top:400px;">
            <hr style="top:405px;">
            <div class="registered"  style="top:390px;width:200px;display:flex;flex-flow:row;gap:1rem;transform-origin: bottom left;transform:rotate(90deg)translatey(-20px);"><h3 style="display:flex;line-height:1;font-weight:800;"> Registered Civil Engineer <br>
Oregon, Washington, California</h3></div>

        </div>
    
    
    </div>
    <footer>
    </footer>
</template>

<script>
export default {
    name: 'app',
    data() {
        return {
            mouseX: 0,
            mouseY: 0,
            intro: true,
            deal: false,
            docs: false,
            centerX: window.innerWidth / 2,
            centerY: window.innerHeight / 2,
            text: '',
            textToCopy: ' ',
            imageUrl: 'path_to_your_image.jpg', // Your image URL here
            imageStyle: {},
            container: null,
            zipInput: '',
            resultMessage: '',
            servedZipCodes: [
                '97030', '97080', '97233', // Existing ZIP codes
                '97024', // Fairview
                '97230', '97236', // Additional Portland ZIP codes
                '97034', '97035', // Lake Oswego ZIP codes
                '97219' // Portland ZIP code overlapping with Lake Oswego
                // Add any more ZIP codes as needed
            ],
        };
    },
    mounted() {

    },
    methods: {
        checkZipCode() {
            let areaServed = this.servedZipCodes.includes(this.zipInput);
            this.resultMessage = areaServed ? "Area Served" : "Area Not Served";
        },
        moveImage(event) {
            const heroElement = this.$refs.hero;
            const rect = heroElement.getBoundingClientRect();
            const x = event.clientX - rect.left - rect.width / 2;
            const y = event.clientY - rect.top - rect.height / 2;

            // Calculate rotation angles
            const rotateX = y / rect.height * 5; // Maximum rotation in degrees
            const rotateY = -x / rect.width * 5;

            // Apply rotation
            this.imageStyle = {
                transform: `perspective(600px) scale(1.4) rotateX(${rotateX}deg) rotateY(${rotateY}deg `,
            };
        },
        getImageDimensions() {
            const imageElement = this.$refs.image;
            if (imageElement) {
                const rect = imageElement.getBoundingClientRect();
                return { width: rect.width, height: rect.height };
            } else {
                return { width: 0, height: 0 };
            }
        },
        async copyToClipboard(text) {
            try {
                await navigator.clipboard.writeText(text);
                console.log('Text copied to clipboard');
                // Optionally, implement a notification to the user
            } catch (err) {
                console.error('Failed to copy: ', err);
                // Optionally, handle the error, like showing an error message
            }
        },
    },
    beforeUnmount() {

    },
}
</script>

<style lang="scss">
 @import url('https://fonts.googleapis.com/css2?family=Barlow:wght@100;200;300;400;500;600;700;800;900&display=swap');


*{    font-family: 'Barlow', sans-serif;
}
h1{}

p{    
    font-family: 'Barlow', sans-serif;
    }

@media (max-width: 900px) {
    
}

/* Add styles for your video player here */
</style>
