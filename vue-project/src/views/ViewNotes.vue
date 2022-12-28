<template>
    <div class="notes">
        <div 
            v-for="i in 3"
            class="card mb-4"
        >
            <div class="card-content">
                <div class="content">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum atque quas facilis sed, provident a animi doloribus consectetur qui fuga laudantium, ipsam aliquid corporis quos! Nulla maiores animi quasi cum.
                </div>
            </div>
            <footer class="card-footer">
                <a href="#" class="card-footer-item">Edit</a>
                <a href="#" class="card-footer-item">Delete</a>
            </footer>
        </div>
    </div>
</template>