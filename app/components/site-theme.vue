<template>

    <div class="uk-margin uk-flex uk-flex-space-between uk-flex-wrap" data-uk-margin>
      <div data-uk-margin>
          <button class="uk-button uk-button-primary" type="submit">{{ 'Save' | trans }}</button>
      </div>
    </div>

    <div class="uk-block uk-block-default uk-text-center">
      <h1>Violoncello Theme Settings</h1>
    </div>

    <div class="uk-block uk-block-muted" style="border:1px solid #ede7e7; padding: 10px;">
      <div class="uk-form uk-form-horizontal">
        <h3>
          Social Links
        </h3>
        <p>Social sharing links presented in the footer:<p>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Facebook url</label>
            <div class="uk-form-controls">
                <input class="uk-width-medium" v-model="config.facebook" type="url">
            </div>
        </div>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Twitter url</label>
            <div class="uk-form-controls">
                <input class="uk-width-medium" v-model="config.twitter" type="url">
            </div>
        </div>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Instagram url</label>
            <div class="uk-form-controls">
                <input class="uk-width-medium" v-model="config.instagram" type="url">
            </div>
        </div>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Github url</label>
            <div class="uk-form-controls">
                <input class="uk-width-medium" v-model="config.github" type="url">
            </div>
        </div>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Youtube url</label>
            <div class="uk-form-controls">
                <input class="uk-width-medium" v-model="config.youtube" type="url">
            </div>
        </div>
        <hr />
        <h3>
          Second Logo
        </h3>
        <p>
          The second logo is positioned at the left side of the navigation bar.<br>
          You can optionally specify a link for the second logo.
        </p>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Second logo</label>
            <div class="uk-form-controls">
                <input-image :source.sync="config.second_logo"></input-image>
            </div>
        </div>
        <div class="uk-form-row">
            <label class="uk-form-label" for="form-h-it">Link for second logo</label>
            <div class="uk-form-controls">
                <input class="uk-width-medium" v-model="config.url_second_logo" type="text">
            </div>
        </div>
      </div>
    </div>

</template>

<script>

    module.exports = {

        section: {
            label: 'Theme',
            icon: 'pk-icon-large-brush',
            priority: 15
        },

        data: function () {
            return _.extend({config: {}}, window.$theme);
        },

        events: {

            save: function() {

                this.$http.post('admin/system/settings/config', {name: this.name, config: this.config}).catch(function (res) {
                    this.$notify(res.data, 'danger');
                });

            }

        }

    };

    window.Site.components['site-theme'] = module.exports;

</script>
