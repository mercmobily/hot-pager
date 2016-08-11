`hot-pager`
Pager element for Hotplate

This is a very simple, basic pager. All it does is display all of the pagerData items, using a dom-repeat template.

A common way of using it is a follows;

    <hot-network target-id="aj" manage-errors>

      <hot-ajax-paging from="0" to="9" per-page="10" current-page="1" pager-data="{{pagerData}}">
        <iron-ajax id="aj" auto url="/stores/polymer" handle-as="json" last-response="{{data}}"></iron-ajax>
      </hot-ajax-paging>

      <template is="dom-repeat" items="[[data]]">
        <paper-card heading="[[item.name]]">
          <div class="card-content">
            <div>Name: <span>{{item.name}}</span></div>
            <div>Surname: <span>{{item.surame}}</span></div>
          </div>
        </paper-card>

      </template>
    </hot-network>

    <hot-pager pager-data="{{pagerData}}" page="{{currentPage}}"></hot-pager>

Here:

* `hot-network` is used to make sure that network resilience is handled. Note that hot-network's target is the `iron-ajax` element.
* The `iron-ajax` element is wrapper with `hot-ajax-paging`. This will make sure that `idon-ajax` has the right headers set for each request, depending of what page is requested.
* The data (coming from the bound property `data` in `iron-ajax`) is displayed with a typical `dom-repeat`
* The pager is used, passing it `pagerData`. Here, `pagerData` will always be changed by `hot-ajax-paging`, and will depend on the page requested by the user as well as the number of results returned by the AJAX query

This is only example code. Custom pagers could show more information (such as the total number of records, etc.) and look very different. This is a basic starting point, where the most commong example of pagination is shown.

Most importantly, _all_ possible calculations are already done in `pagerData`.

