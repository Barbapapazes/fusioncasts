<php>
use function \Fusion\{prop};
use \App\Models\Podcast;
use Illuminate\Support\Str;

$podcast = prop()->fromRoute(class: Podcast::class)->readonly();

expose(changePodcastTitle: function() use ($podcast) {
  $podcast->title = Str::random(10);
  $podcast->save();
  return $podcast;
});
</php>

<template>
  Podcast: {{ podcast.title }}

  <button class="bg-blue-500 text-white p-2" @click="changePodcastTitle({ changePodcastTitle }).then(p => podcast.title = p.title)">
    Change podcast title
  </button>
</template>
