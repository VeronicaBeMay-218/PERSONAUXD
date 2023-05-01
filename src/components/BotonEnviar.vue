<script>

export default {
    props: ['desactivar'],
}
</script>

<template>
    <div class="flex justify-center items-center space-x-4 text-base my-8">
        <button class="px-4 py-1 text-black font-bold tracking-wider bg-gray-200 hover:bg-blue-100 rounded" type="button">
            <slot></slot>
        </button>
    </div>
</template>