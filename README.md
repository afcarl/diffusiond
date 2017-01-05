
[DEPRECATED, CLICK ME TO GO TO THE NEW REPO](https://github.com/idekerlab/diffusiond)

Diffusiond
==========
Provides a daemon capable of servicing heat diffusion tasks on networks provided as cx or stored in NDEx.  For details see the manuscript "Network propagation in the Cytoscape Cyberinfrastructure. Carlin DE et al. Submitted to PLoS Computational Biology."

POST diffuse.cytoscape.io
-------------------------
The only route provided by this service is / the top level. Use this route to diffuse a vector of node heats against a network.

Body
----

MIME type must be `applicaiton/json`

The body must be a CX document, which will be encoded as JSON. If a heatvector is not given in the query string parameters, at least
one node needs to have a node attribute called 'diffusion_input' or whatever the query string parameter heatattribute is set to. The value
of this attribute must be a Double in the range 0 to 1 representing the initial node heat.

Parameters
----------

| Key           | Type         | Default Value       | Description                                                        |
| ------------- | :----------: | :-----------------: | :----------------------------------------------------------------- |
| subnetworkid  | Integer      | None                | A Cytoscape subnetwork to be extracted from a Collection           |
| time          | Double       | 0.1                 | Parameter t from equation 1 of the manuscript to indicate the extent of spread over the network |
| kernel        | Boolean      | False               | Should the diffuser calculate an intermediate kernel               |
| heatvector    | List or Dict | None                | Node heats encoded in the query string, overrides CX encoded heats |
| heatattribute | String       | 'diffusion_input'   | The node attribute that contains the initial node heat as a Double |
| normalize     | Boolean      | False               | Should the Laplacian matrix be normalized                         |
