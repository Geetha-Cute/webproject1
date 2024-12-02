 // JavaScript to handle the expansion of the details
 document.addEventListener("DOMContentLoaded", function () {
    const radioButtons = document.querySelectorAll('input[type="radio"][name="bundle"]');

    radioButtons.forEach(radio => {
        radio.addEventListener("change", function () {
            
            // Hide all pair-details
            document.querySelectorAll(".pair-details").forEach(detail => {
                detail.style.display = "none";
            });

            // Reset background color of previously selected radio button's parent
            radioButtons.forEach(rb => {
                if (rb !== radio) {
                    const parent = rb.closest(".bundle-option");
                    parent.style.backgroundColor = "";
                    parent.style.borderColor = "";
                    parent.style.border = "";
                }
            });

            // Show the selected radio button's details
            const parent = radio.closest(".bundle-option");
            const details = parent.querySelector(".pair-details");

            if (details) {
                details.style.display = "block";
                parent.style.backgroundColor = "#fff5f7";
                parent.style.borderColor = "#ff69b4";
                parent.style.border = "3px solid #ff69b4";
                const parentMostPopular = parent.querySelector(".most-popular");
                parentMostPopular.style.top = "-7%";
            }
        });
    });

    // Trigger change event on the default checked radio button
    const defaultChecked = document.querySelector('input[type="radio"][name="bundle"]:checked');
    if (defaultChecked) {
        defaultChecked.dispatchEvent(new Event("change"));
    }
});