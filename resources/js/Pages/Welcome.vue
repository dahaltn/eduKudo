<script setup>
import {Head, Link} from '@inertiajs/vue3';
import ParentComponent from "@/EduKudoComponents/ParentComponent.vue";
import LessEditorComponent from "@/EduKudoComponents/LessEditorComponent.vue";

</script>

<template>
    <Head title="Welcome EduKUDO Test"/>

    <div class="flex flex-col items-center min-h-screen bg-gray-100">
        <!-- Navigation Bar -->
        <nav v-if="canLogin" class="w-full bg-gray-200 shadow-md py-4 px-6 flex justify-center">
            <div class="w-4/5 flex justify-end">
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70"
                >
                    Dashboard
                </Link>

                <template v-else>
                    <Link
                        :href="route('login')"
                        class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20]"
                    >
                        Log in
                    </Link>

                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20]"
                    >
                        Register
                    </Link>
                </template>
            </div>
        </nav>

        <!-- Main Content -->
        <main class="w-4/5 bg-white shadow-lg rounded-lg p-8 mt-6">
            <h1 class="text-2xl font-bold text-center">Welcome to EduKUDO Test</h1>
            <div class="mt-4 p-4">
                <div>
                    <h2 class="font-bold text-2xl">Tasks Overview</h2>

                    <h3 class="font-bold mt-4">Task 1: Parent and Child Components</h3>
                    <ul class="list-disc pl-6">
                        <li>Created a parent component with two variables: a boolean and a string.</li>
                        <li>Child component:
                            <ul class="list-disc pl-6">
                                <li>Toggles the boolean value.</li>
                                <li>Updates the string via a text box.</li>
                            </ul>
                        </li>
                        <li>Used props and events for communication between parent and child.</li>
                    </ul>

                    <h3 class="font-bold mt-4">Task 2: LESS Compiler and Live Preview</h3>
                    <ul class="list-disc pl-6">
                        <li>Built a real-time editor with:
                            <ul class="list-disc pl-6">
                                <li>Input for HTML and LESS.</li>
                                <li>Live LESS compilation (debounced).</li>
                                <li>Isolated preview area with scoped styles.</li>
                            </ul>
                        </li>
                        <li>Preview dynamically updates based on inputs.</li>
                    </ul>
                </div>
                <h3 class="font-bold mt-4">Files:</h3>
                <ul class="list-disc pl-6">
                    <li> <span class="font-bold">Main Component:</span>
                        <ul class="list-disc pl-6">
                            <li>
                                resources/js/Pages/Welcome.vue
                            </li>
                        </ul>
                    </li>
                    <li><span class="font-bold">Parent and Child Components:</span>
                        <ul class="list-disc pl-6">
                            <li>
                                resources/js/EduKudoComponents/ParentComponent.vue
                            </li>
                            <li>
                                resources/js/EduKudoComponents/ChildComponent.vue
                            </li>
                        </ul>
                    </li>
                    <li> <span class="font-bold">LESS Editor:</span>
                        <ul class="list-disc pl-6">
                            <li>
                                resources/js/EduKudoComponents/LessEditorComponent.vue
                            </li>
                        </ul>
                    </li>
                </ul>

            </div>

            <!-- Task 1 Section -->
            <div class="w-full bg-gray-50 shadow-inner rounded-md p-6 mt-8">
                <h2 class="text-lg font-semibold mb-4">Task 1: Parent & child components communication:</h2>
                <ParentComponent/>
            </div>

            <!-- Task 2 Section -->
            <div class="w-full bg-gray-50 shadow-inner rounded-md p-6 mt-8">
                <h2 class="text-lg font-semibold mb-4">Task 2: LESS and HTML Preview ( path:
                    resources/js/EduKudoComponents/LessEditorComponent.vue)</h2>
                <LessEditorComponent/>
            </div>


            <div class="flex justify-center mt-6">
                <p class="text-center font-bold">Task done by: <span class="italic">
        Tej Dahal </span></p>
            </div>

        </main>


        <!-- Footer -->
        <footer
            class="py-8 text-center text-sm text-black">
            EduKUDO Dev Challenge {{ new Date().getFullYear() }}, all rights reserved.
        </footer>
    </div>
</template>
