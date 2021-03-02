# Module titiler.endpoints.factory

TiTiler Router factories.

None

## Variables

```python3
MAX_THREADS
```

```python3
img_endpoint_params
```

## Classes

### BaseTilerFactory

```python3
class BaseTilerFactory(
    reader: Type[rio_tiler.io.base.BaseReader],
    reader_options: Dict = <factory>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Type[titiler.dependencies.PathParams] = <class 'titiler.dependencies.PathParams'>,
    dataset_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.DatasetParams'>,
    layer_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.BidxExprParams'>,
    render_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.RenderParams'>,
    tms_dependency: Callable[..., morecantile.models.TileMatrixSet] = <function WebMercatorTMSParams at 0x7f1b4ff9f280>,
    additional_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7f1b4fda9700>,
    router_prefix: str = '',
    gdal_config: Dict = <factory>,
    optional_headers: List[titiler.resources.enums.OptionalHeaders] = <factory>
)
```

#### Descendants

* titiler.endpoints.factory.TilerFactory
* titiler.endpoints.factory.MosaicTilerFactory

#### Class variables

```python3
dataset_dependency
```

```python3
layer_dependency
```

```python3
path_dependency
```

```python3
render_dependency
```

```python3
router_prefix
```

#### Methods

    
#### additional_dependency

```python3
def additional_dependency(
    
)
```

    

    
#### register_routes

```python3
def register_routes(
    self
)
```

    
Register Tiler Routes.

    
#### tms_dependency

```python3
def tms_dependency(
    TileMatrixSetId: titiler.dependencies.WebMercatorTileMatrixSetName = Query(WebMercatorTileMatrixSetName.WebMercatorQuad)
) -> morecantile.models.TileMatrixSet
```

    
TileMatrixSet Dependency.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

    
Return full url (with prefix) for a specific endpoint.

### MosaicTilerFactory

```python3
class MosaicTilerFactory(
    reader: Type[cogeo_mosaic.backends.base.BaseBackend] = <function MosaicBackend at 0x7f1b4fe54550>,
    reader_options: Dict = <factory>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Type[titiler.dependencies.PathParams] = <class 'titiler.dependencies.PathParams'>,
    dataset_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.DatasetParams'>,
    layer_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.BidxExprParams'>,
    render_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.RenderParams'>,
    tms_dependency: Callable[..., morecantile.models.TileMatrixSet] = <function WebMercatorTMSParams at 0x7f1b4ff9f280>,
    additional_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7f1b4fda9700>,
    router_prefix: str = '',
    gdal_config: Dict = <factory>,
    optional_headers: List[titiler.resources.enums.OptionalHeaders] = <factory>,
    dataset_reader: Type[rio_tiler.io.base.BaseReader] = <class 'rio_tiler.io.cogeo.COGReader'>,
    backend_options: Dict = <factory>
)
```

#### Ancestors (in MRO)

* titiler.endpoints.factory.BaseTilerFactory

#### Class variables

```python3
dataset_dependency
```

```python3
dataset_reader
```

```python3
layer_dependency
```

```python3
path_dependency
```

```python3
render_dependency
```

```python3
router_prefix
```

#### Methods

    
#### additional_dependency

```python3
def additional_dependency(
    
)
```

    

    
#### bounds

```python3
def bounds(
    self
)
```

    
Register /bounds endpoint.

    
#### info

```python3
def info(
    self
)
```

    
Register /info endpoint

    
#### point

```python3
def point(
    self
)
```

    
Register /point endpoint.

    
#### read

```python3
def read(
    self
)
```

    
Register / (Get) Read endpoint.

    
#### reader

```python3
def reader(
    url: str,
    *args: Any,
    **kwargs: Any
) -> cogeo_mosaic.backends.base.BaseBackend
```

    
Select mosaic backend for url.

    
#### register_routes

```python3
def register_routes(
    self
)
```

    
This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialisation.

    
#### tile

```python3
def tile(
    self
)
```

    
Register /tiles endpoints.

    
#### tilejson

```python3
def tilejson(
    self
)
```

    
Add tilejson endpoint.

    
#### tms_dependency

```python3
def tms_dependency(
    TileMatrixSetId: titiler.dependencies.WebMercatorTileMatrixSetName = Query(WebMercatorTileMatrixSetName.WebMercatorQuad)
) -> morecantile.models.TileMatrixSet
```

    
TileMatrixSet Dependency.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

    
Return full url (with prefix) for a specific endpoint.

    
#### validate

```python3
def validate(
    self
)
```

    
Register /validate endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

    
Add wmts endpoint.

### MultiBandTilerFactory

```python3
class MultiBandTilerFactory(
    reader: Type[rio_tiler.io.base.MultiBandReader] = <class 'rio_tiler.io.cogeo.COGReader'>,
    reader_options: Dict = <factory>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Type[titiler.dependencies.PathParams] = <class 'titiler.dependencies.PathParams'>,
    dataset_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.DatasetParams'>,
    layer_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.BandsExprParams'>,
    render_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.RenderParams'>,
    tms_dependency: Callable[..., morecantile.models.TileMatrixSet] = <function TMSParams at 0x7f1b4ff9f310>,
    additional_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7f1b4fda9700>,
    router_prefix: str = '',
    gdal_config: Dict = <factory>,
    optional_headers: List[titiler.resources.enums.OptionalHeaders] = <factory>,
    metadata_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.MetadataParams'>,
    img_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.ImageParams'>,
    add_preview: bool = True,
    add_part: bool = True
)
```

#### Ancestors (in MRO)

* titiler.endpoints.factory.TilerFactory
* titiler.endpoints.factory.BaseTilerFactory

#### Class variables

```python3
add_part
```

```python3
add_preview
```

```python3
dataset_dependency
```

```python3
img_dependency
```

```python3
layer_dependency
```

```python3
metadata_dependency
```

```python3
path_dependency
```

```python3
reader
```

```python3
render_dependency
```

```python3
router_prefix
```

#### Methods

    
#### additional_dependency

```python3
def additional_dependency(
    
)
```

    

    
#### bounds

```python3
def bounds(
    self
)
```

    
Register /bounds endpoint.

    
#### info

```python3
def info(
    self
)
```

    
Register /info endpoint.

    
#### metadata

```python3
def metadata(
    self
)
```

    
Register /metadata endpoint.

    
#### part

```python3
def part(
    self
)
```

    
Register /crop endpoint.

    
#### point

```python3
def point(
    self
)
```

    
Register /point endpoints.

    
#### preview

```python3
def preview(
    self
)
```

    
Register /preview endpoint.

    
#### register_routes

```python3
def register_routes(
    self
)
```

    
This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialisation.

    
#### tile

```python3
def tile(
    self
)
```

    
Register /tiles endpoint.

    
#### tilejson

```python3
def tilejson(
    self
)
```

    
Register /tilejson.json endpoint.

    
#### tms_dependency

```python3
def tms_dependency(
    TileMatrixSetId: titiler.dependencies.TileMatrixSetNames = Query(TileMatrixSetNames.WebMercatorQuad)
) -> morecantile.models.TileMatrixSet
```

    
TileMatrixSet Dependency.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

    
Return full url (with prefix) for a specific endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

    
Register /wmts endpoint.

### MultiBaseTilerFactory

```python3
class MultiBaseTilerFactory(
    reader: Type[rio_tiler.io.base.MultiBaseReader] = <class 'rio_tiler.io.cogeo.COGReader'>,
    reader_options: Dict = <factory>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Type[titiler.dependencies.PathParams] = <class 'titiler.dependencies.PathParams'>,
    dataset_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.DatasetParams'>,
    layer_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.AssetsBidxExprParams'>,
    render_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.RenderParams'>,
    tms_dependency: Callable[..., morecantile.models.TileMatrixSet] = <function TMSParams at 0x7f1b4ff9f310>,
    additional_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7f1b4fda9700>,
    router_prefix: str = '',
    gdal_config: Dict = <factory>,
    optional_headers: List[titiler.resources.enums.OptionalHeaders] = <factory>,
    metadata_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.MetadataParams'>,
    img_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.ImageParams'>,
    add_preview: bool = True,
    add_part: bool = True
)
```

#### Ancestors (in MRO)

* titiler.endpoints.factory.TilerFactory
* titiler.endpoints.factory.BaseTilerFactory

#### Class variables

```python3
add_part
```

```python3
add_preview
```

```python3
dataset_dependency
```

```python3
img_dependency
```

```python3
layer_dependency
```

```python3
metadata_dependency
```

```python3
path_dependency
```

```python3
reader
```

```python3
render_dependency
```

```python3
router_prefix
```

#### Methods

    
#### additional_dependency

```python3
def additional_dependency(
    
)
```

    

    
#### bounds

```python3
def bounds(
    self
)
```

    
Register /bounds endpoint.

    
#### info

```python3
def info(
    self
)
```

    
Register /info endpoint.

    
#### metadata

```python3
def metadata(
    self
)
```

    
Register /metadata endpoint.

    
#### part

```python3
def part(
    self
)
```

    
Register /crop endpoint.

    
#### point

```python3
def point(
    self
)
```

    
Register /point endpoints.

    
#### preview

```python3
def preview(
    self
)
```

    
Register /preview endpoint.

    
#### register_routes

```python3
def register_routes(
    self
)
```

    
This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialisation.

    
#### tile

```python3
def tile(
    self
)
```

    
Register /tiles endpoint.

    
#### tilejson

```python3
def tilejson(
    self
)
```

    
Register /tilejson.json endpoint.

    
#### tms_dependency

```python3
def tms_dependency(
    TileMatrixSetId: titiler.dependencies.TileMatrixSetNames = Query(TileMatrixSetNames.WebMercatorQuad)
) -> morecantile.models.TileMatrixSet
```

    
TileMatrixSet Dependency.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

    
Return full url (with prefix) for a specific endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

    
Register /wmts endpoint.

### TMSFactory

```python3
class TMSFactory(
    supported_tms: Type[titiler.dependencies.TileMatrixSetNames] = <enum 'TileMatrixSetNames'>,
    tms_dependency: Callable[..., morecantile.models.TileMatrixSet] = <function TMSParams at 0x7f1b4ff9f310>,
    router: fastapi.routing.APIRouter = <factory>,
    router_prefix: str = ''
)
```

#### Class variables

```python3
router_prefix
```

```python3
supported_tms
```

#### Methods

    
#### register_routes

```python3
def register_routes(
    self
)
```

    
Register TMS endpoint routes.

    
#### tms_dependency

```python3
def tms_dependency(
    TileMatrixSetId: titiler.dependencies.TileMatrixSetNames = Query(TileMatrixSetNames.WebMercatorQuad)
) -> morecantile.models.TileMatrixSet
```

    
TileMatrixSet Dependency.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

    
Return full url (with prefix) for a specific endpoint.

### TilerFactory

```python3
class TilerFactory(
    reader: Type[rio_tiler.io.base.BaseReader] = <class 'rio_tiler.io.cogeo.COGReader'>,
    reader_options: Dict = <factory>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Type[titiler.dependencies.PathParams] = <class 'titiler.dependencies.PathParams'>,
    dataset_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.DatasetParams'>,
    layer_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.BidxExprParams'>,
    render_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.RenderParams'>,
    tms_dependency: Callable[..., morecantile.models.TileMatrixSet] = <function TMSParams at 0x7f1b4ff9f310>,
    additional_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7f1b4fda9700>,
    router_prefix: str = '',
    gdal_config: Dict = <factory>,
    optional_headers: List[titiler.resources.enums.OptionalHeaders] = <factory>,
    metadata_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.MetadataParams'>,
    img_dependency: Type[titiler.dependencies.DefaultDependency] = <class 'titiler.dependencies.ImageParams'>,
    add_preview: bool = True,
    add_part: bool = True
)
```

#### Ancestors (in MRO)

* titiler.endpoints.factory.BaseTilerFactory

#### Descendants

* titiler.endpoints.factory.MultiBaseTilerFactory
* titiler.endpoints.factory.MultiBandTilerFactory

#### Class variables

```python3
add_part
```

```python3
add_preview
```

```python3
dataset_dependency
```

```python3
img_dependency
```

```python3
layer_dependency
```

```python3
metadata_dependency
```

```python3
path_dependency
```

```python3
reader
```

```python3
render_dependency
```

```python3
router_prefix
```

#### Methods

    
#### additional_dependency

```python3
def additional_dependency(
    
)
```

    

    
#### bounds

```python3
def bounds(
    self
)
```

    
Register /bounds endpoint.

    
#### info

```python3
def info(
    self
)
```

    
Register /info endpoint.

    
#### metadata

```python3
def metadata(
    self
)
```

    
Register /metadata endpoint

    
#### part

```python3
def part(
    self
)
```

    
Register /crop endpoint.

    
#### point

```python3
def point(
    self
)
```

    
Register /point endpoints.

    
#### preview

```python3
def preview(
    self
)
```

    
Register /preview endpoint.

    
#### register_routes

```python3
def register_routes(
    self
)
```

    
This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialisation.

    
#### tile

```python3
def tile(
    self
)
```

    
Register /tiles endpoint.

    
#### tilejson

```python3
def tilejson(
    self
)
```

    
Register /tilejson.json endpoint.

    
#### tms_dependency

```python3
def tms_dependency(
    TileMatrixSetId: titiler.dependencies.TileMatrixSetNames = Query(TileMatrixSetNames.WebMercatorQuad)
) -> morecantile.models.TileMatrixSet
```

    
TileMatrixSet Dependency.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

    
Return full url (with prefix) for a specific endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

    
Register /wmts endpoint.