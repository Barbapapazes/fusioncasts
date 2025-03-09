<php>
use function \Fusion\{prop};

$count = prop(0);

expose(add: function() use ($count) {
    $count = $count + 1;
    return $count;
});
</php>

<template>
    <div class="text-3xl">
        {{ count }}
    </div>
    <button class="bg-blue-500 text-white p-2" @click="add({ add }).then(value => count = value)">
        Add
    </button>
</template>
