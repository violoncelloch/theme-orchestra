<template>

    <div class="uk-block uk-block-default uk-text-center">
      <h1>Violoncello Widget Settings</h1>
    </div>
    <div class="uk-block uk-block-muted" style="border:1px solid #ede7e7; padding: 10px;">
      <div class="uk-form uk-form-horizontal">
        <div v-if="widget.position == 'flyer' || widget.position =='flyerarchive'">
          <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Flyer image</label>
            <div class="uk-form-controls">
              <input-image :source.sync="widget.theme.flyer_image"></input-image>
            </div>
          </div>
          <div v-if="widget.theme.flyer_image">
            <div class="uk-form-row">
              <label class="uk-form-label" for="form-h-it">Link to Flyer or PDF</label>
              <div class="uk-form-controls">
                <input-link class="uk-width-1-2" :link.sync="widget.theme.flyer_link"></input-link>
              </div>
            </div>
            <div class="uk-form-row">
                <label class="uk-form-label" for="form-h-it">Disable Popup</label>
                <div class="uk-form-controls">
                  <input class="uk-width-medium" v-model="widget.theme.content_disabled" type="checkbox">
                </div>
            </div>
          </div>
          <hr>
        </div>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Hide widget title</label>
            <div class="uk-form-controls">
              <input class="uk-width-medium" v-model="widget.theme.title_hide" type="checkbox">
            </div>
        </div>
        <div v-if="widget.position !== 'flyer' && widget.position !== 'flyerarchive'">
          <div v-if="widget.position !== 'titleimage'" class="uk-form-row">
              <label class="uk-form-label" for="form-h-it">Card style</label>
              <div class="uk-form-controls">
                <select class="uk-width-1-2" v-model="widget.theme.card_style">
                  <option value="">no card (style)</option>
                  <option value="uk-card-default">default card style</option>
                  <option value="uk-card-primary">primary card style</option>
                  <option value="uk-card-secondary">secondary card style</option>
                </select>
              </div>
          </div>
          <div v-if="widget.position !== 'titleimage' && widget.theme.card_style !== ''" class="uk-form-row">
              <label class="uk-form-label" for="form-h-it">Card padding</label>
              <div class="uk-form-controls">
                <select class="uk-width-1-2" v-model="widget.theme.card_padding">
                  <option value="">no padding</option>
                  <option value="uk-card-body">normal body padding</option>
                </select>
              </div>
          </div>
          <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Widget background image</label>
            <div class="uk-form-controls">
              <input-image :source.sync="widget.theme.card_image"></input-image>
            </div>
          </div>
        </div>
      </div>
    </div>

</template>

<script>
    module.exports = {
        section: {
            label: 'Theme',
            priority: 90
        },
        props: ['widget', 'config']
    };
    window.Widgets.components['theme'] = module.exports;
</script>
