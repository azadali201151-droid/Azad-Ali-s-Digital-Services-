/**
 * =========================================================================
 * 1. DYNAMIC CALCULATOR MODULE MECHANICS
 * =========================================================================
 */
function updateTotalEstimate() {
    const webElement = document.getElementById('service-select');
    const designElement = document.getElementById('design-select');
    const marketingElement = document.getElementById('marketing-select');


    // Safe extraction of targeted configuration element metrics
    const webPrice = parseFloat(webElement.options[webElement.selectedIndex].getAttribute('data-price')) || 0;
    const designPrice = parseFloat(designElement.options[designElement.selectedIndex].getAttribute('data-price')) || 0;
    const marketingPrice = parseFloat(marketingElement.options[marketingElement.selectedIndex].getAttribute('data-price')) || 0;


    // Direct sum compilation processing values
    const currentTotal = webPrice + designPrice + marketingPrice;
    document.getElementById('total-price-display').innerText = `$${currentTotal}`;
}


/**
 * Builds custom client configuration array text values and passes them to WhatsApp routing endpoints
 */
function submitOrderViaWhatsApp() {
    const webElement = document.getElementById('service-select');
    const designElement = document.getElementById('design-select');
    const marketingElement = document.getElementById('marketing-select');


    const webText = webElement.options[webElement.selectedIndex].text;
    const designText = designElement.options[designElement.selectedIndex].text;
    const marketingText = marketingElement.options[marketingElement.selectedIndex].text;
    const currentPriceText = document.getElementById('total-price-display').innerText;


    // URL safe encoding structure configuration mapping
    const structuredWhatsAppMsg = `Hello Azad Ali, I calculated a project package quote configuration on your platform:%0A%0A` +
                                   `- Web Layout: ${webText}%0A` +
                                   `- Design Aspect: ${designText}%0A` +
                                   `- Marketing Plan: ${marketingText}%0A%0A` +
                                   `Total Estimated Value Request: ${currentPriceText}`;


    window.open(`https://wa.me/923141201151?text=${structuredWhatsAppMsg}`, '_blank');
}


/**
 * =========================================================================
 * 2. FAQ ACCORDION DISPLAY TRIGGERS
 * =========================================================================
 */
const faqQuestions = document.querySelectorAll('.faq-question');


faqQuestions.forEach(question => {
    question.addEventListener('click', () => {
        const answer = question.nextElementSibling;


        if (answer.style.display === 'block') {
            answer.style.display = 'none';
        } else {
            answer.style.display = 'block';
        }
    });
});


/**
 * =========================================================================
 * 3. STICKY DYNAMIC NAVIGATION SCROLL SWAPPER
 * =========================================================================
 */
window.addEventListener('scroll', function(){
    const nav = document.querySelector('nav');


    if (window.scrollY > 50) {
        nav.style.background = 'rgba(2,6,23,0.98)';
    } else {
        nav.style.background = 'rgba(5,10,20,0.92)';
    }
});



