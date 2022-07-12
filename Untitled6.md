```python
pip install folium
```

    Collecting folium
      Downloading folium-0.12.1.post1-py2.py3-none-any.whl (95 kB)
    [K     |████████████████████████████████| 95 kB 3.4 MB/s eta 0:00:011
    [?25hRequirement already satisfied: requests in ./opt/anaconda3/lib/python3.9/site-packages (from folium) (2.27.1)
    Collecting branca>=0.3.0
      Downloading branca-0.5.0-py3-none-any.whl (24 kB)
    Requirement already satisfied: numpy in ./opt/anaconda3/lib/python3.9/site-packages (from folium) (1.21.5)
    Requirement already satisfied: jinja2>=2.9 in ./opt/anaconda3/lib/python3.9/site-packages (from folium) (2.11.3)
    Requirement already satisfied: MarkupSafe>=0.23 in ./opt/anaconda3/lib/python3.9/site-packages (from jinja2>=2.9->folium) (2.0.1)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in ./opt/anaconda3/lib/python3.9/site-packages (from requests->folium) (1.26.9)
    Requirement already satisfied: charset-normalizer~=2.0.0 in ./opt/anaconda3/lib/python3.9/site-packages (from requests->folium) (2.0.4)
    Requirement already satisfied: idna<4,>=2.5 in ./opt/anaconda3/lib/python3.9/site-packages (from requests->folium) (3.3)
    Requirement already satisfied: certifi>=2017.4.17 in ./opt/anaconda3/lib/python3.9/site-packages (from requests->folium) (2021.10.8)
    Installing collected packages: branca, folium
    Successfully installed branca-0.5.0 folium-0.12.1.post1
    Note: you may need to restart the kernel to use updated packages.



```python
import numpy as np
import pandas as pd
import folium as fo
data = pd.read_csv("https://raw.githubusercontent.com/amankharwal/Website-data/master/Volcano.csv")
print(data.head())
```

       Year  Month   Day  TSU   EQ                    Name              Location  \
    0  2010      1   NaN  NaN  NaN              Tungurahua               Ecuador   
    1  2010      3  31.0  NaN  NaN        Eyjafjallajokull             Iceland-S   
    2  2010      5  27.0  NaN  NaN                  Pacaya             Guatemala   
    3  2010      5  29.0  TSU   EQ                 Sarigan  Mariana Is-C Pacific   
    4  2010      8   6.0  NaN  NaN  Karangetang [Api Siau]  Sangihe Is-Indonesia   
    
             Country  Latitude  Longitude  ...  TOTAL_DEATHS  \
    0        Ecuador    -1.467    -78.442  ...           NaN   
    1        Iceland    63.630    -19.620  ...           2.0   
    2      Guatemala    14.381    -90.601  ...           1.0   
    3  United States    16.708    145.780  ...           NaN   
    4      Indonesia     2.780    125.480  ...           4.0   
    
      TOTAL_DEATHS_DESCRIPTION TOTAL_MISSING TOTAL_MISSING_DESCRIPTION  \
    0                      NaN           NaN                       NaN   
    1                      1.0           NaN                       NaN   
    2                      1.0           3.0                       1.0   
    3                      NaN           NaN                       NaN   
    4                      1.0           NaN                       NaN   
    
       TOTAL_INJURIES TOTAL_INJURIES_DESCRIPTION  TOTAL_DAMAGE_MILLIONS_DOLLARS  \
    0             NaN                        NaN                            NaN   
    1             NaN                        NaN                            NaN   
    2             NaN                        NaN                            NaN   
    3             NaN                        NaN                            NaN   
    4             5.0                        1.0                            NaN   
    
       TOTAL_DAMAGE_DESCRIPTION  TOTAL_HOUSES_DESTROYED  \
    0                       1.0                     NaN   
    1                       NaN                     NaN   
    2                       1.0                     3.0   
    3                       NaN                     NaN   
    4                       NaN                     NaN   
    
       TOTAL_HOUSES_DESTROYED_DESCRIPTION  
    0                                 NaN  
    1                                 NaN  
    2                                 1.0  
    3                                 NaN  
    4                                 1.0  
    
    [5 rows x 36 columns]



```python
lat = list(data["Latitude"])
lon = list(data["Longitude"])
name = list(data["Name"])

volcano = fo.FeatureGroup(name="Volcano")
for a, b, c in zip(lat, lon, name):
  volcano.add_child(fo.Marker(location=[a, b], popup=c, icon=fo.Icon(color='blue')))
  
fo.Map().add_child(volcano)
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe srcdoc="&lt;!DOCTYPE html&gt;
&lt;head&gt;    
    &lt;meta http-equiv=&quot;content-type&quot; content=&quot;text/html; charset=UTF-8&quot; /&gt;

        &lt;script&gt;
            L_NO_TOUCH = false;
            L_DISABLE_3D = false;
        &lt;/script&gt;

    &lt;style&gt;html, body {width: 100%;height: 100%;margin: 0;padding: 0;}&lt;/style&gt;
    &lt;style&gt;#map {position:absolute;top:0;bottom:0;right:0;left:0;}&lt;/style&gt;
    &lt;script src=&quot;https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://code.jquery.com/jquery-1.12.4.min.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js&quot;&gt;&lt;/script&gt;
    &lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js&quot;&gt;&lt;/script&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdn.jsdelivr.net/npm/leaflet@1.6.0/dist/leaflet.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css&quot;/&gt;
    &lt;link rel=&quot;stylesheet&quot; href=&quot;https://cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css&quot;/&gt;

            &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width,
                initial-scale=1.0, maximum-scale=1.0, user-scalable=no&quot; /&gt;
            &lt;style&gt;
                #map_370082fa95dd0997170ba7b8d02e5b34 {
                    position: relative;
                    width: 100.0%;
                    height: 100.0%;
                    left: 0.0%;
                    top: 0.0%;
                }
            &lt;/style&gt;

&lt;/head&gt;
&lt;body&gt;    

            &lt;div class=&quot;folium-map&quot; id=&quot;map_370082fa95dd0997170ba7b8d02e5b34&quot; &gt;&lt;/div&gt;

&lt;/body&gt;
&lt;script&gt;    

            var map_370082fa95dd0997170ba7b8d02e5b34 = L.map(
                &quot;map_370082fa95dd0997170ba7b8d02e5b34&quot;,
                {
                    center: [0, 0],
                    crs: L.CRS.EPSG3857,
                    zoom: 1,
                    zoomControl: true,
                    preferCanvas: false,
                }
            );





            var tile_layer_c3bb86493de2de34c8db3220f62aa4dd = L.tileLayer(
                &quot;https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png&quot;,
                {&quot;attribution&quot;: &quot;Data by \u0026copy; \u003ca href=\&quot;http://openstreetmap.org\&quot;\u003eOpenStreetMap\u003c/a\u003e, under \u003ca href=\&quot;http://www.openstreetmap.org/copyright\&quot;\u003eODbL\u003c/a\u003e.&quot;, &quot;detectRetina&quot;: false, &quot;maxNativeZoom&quot;: 18, &quot;maxZoom&quot;: 18, &quot;minZoom&quot;: 0, &quot;noWrap&quot;: false, &quot;opacity&quot;: 1, &quot;subdomains&quot;: &quot;abc&quot;, &quot;tms&quot;: false}
            ).addTo(map_370082fa95dd0997170ba7b8d02e5b34);


            var feature_group_bc7dabeecca361cb29368f22f5f10a4c = L.featureGroup(
                {}
            ).addTo(map_370082fa95dd0997170ba7b8d02e5b34);


            var marker_181af3bd34394712e3848610bab87fdc = L.marker(
                [-1.467, -78.442],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_82c6cebf3142317fb82dda7a17d00966 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_181af3bd34394712e3848610bab87fdc.setIcon(icon_82c6cebf3142317fb82dda7a17d00966);


        var popup_65f264d2f2867d5446d2fe006cd84dd3 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_b8bebcc437550e5695bf9e5e0d8579ca = $(`&lt;div id=&quot;html_b8bebcc437550e5695bf9e5e0d8579ca&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Tungurahua&lt;/div&gt;`)[0];
            popup_65f264d2f2867d5446d2fe006cd84dd3.setContent(html_b8bebcc437550e5695bf9e5e0d8579ca);


        marker_181af3bd34394712e3848610bab87fdc.bindPopup(popup_65f264d2f2867d5446d2fe006cd84dd3)
        ;




            var marker_0eaddedc08bc70468c6b6dcd4a0ca84b = L.marker(
                [63.63, -19.62],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_06817721bd3c8b33db91726d42bee877 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_0eaddedc08bc70468c6b6dcd4a0ca84b.setIcon(icon_06817721bd3c8b33db91726d42bee877);


        var popup_b8761670f0c4a6d3987f598921ef1601 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_3d09f912ef61af11b20f8079f69ecb29 = $(`&lt;div id=&quot;html_3d09f912ef61af11b20f8079f69ecb29&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Eyjafjallajokull&lt;/div&gt;`)[0];
            popup_b8761670f0c4a6d3987f598921ef1601.setContent(html_3d09f912ef61af11b20f8079f69ecb29);


        marker_0eaddedc08bc70468c6b6dcd4a0ca84b.bindPopup(popup_b8761670f0c4a6d3987f598921ef1601)
        ;




            var marker_be0c516c38d5cca1415824fe30156185 = L.marker(
                [14.381, -90.601],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_3f92f4934b85d8af4bbc3006ae6be185 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_be0c516c38d5cca1415824fe30156185.setIcon(icon_3f92f4934b85d8af4bbc3006ae6be185);


        var popup_03722d2c6931fbb09f04b6ace02415cf = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_8eb8fa022d72d5f996cecfa199b8c1bd = $(`&lt;div id=&quot;html_8eb8fa022d72d5f996cecfa199b8c1bd&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Pacaya&lt;/div&gt;`)[0];
            popup_03722d2c6931fbb09f04b6ace02415cf.setContent(html_8eb8fa022d72d5f996cecfa199b8c1bd);


        marker_be0c516c38d5cca1415824fe30156185.bindPopup(popup_03722d2c6931fbb09f04b6ace02415cf)
        ;




            var marker_bd708cd7d731d1e0c657e4b0d133cab4 = L.marker(
                [16.708, 145.78],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_a63c47235607269487bbad4f5cfb5c91 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_bd708cd7d731d1e0c657e4b0d133cab4.setIcon(icon_a63c47235607269487bbad4f5cfb5c91);


        var popup_d28fe915b4ce6ccaa80fa0850f831164 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_fde0108b585b882e3eb4eee99cd5299d = $(`&lt;div id=&quot;html_fde0108b585b882e3eb4eee99cd5299d&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sarigan&lt;/div&gt;`)[0];
            popup_d28fe915b4ce6ccaa80fa0850f831164.setContent(html_fde0108b585b882e3eb4eee99cd5299d);


        marker_bd708cd7d731d1e0c657e4b0d133cab4.bindPopup(popup_d28fe915b4ce6ccaa80fa0850f831164)
        ;




            var marker_988d8f97f7f46f7011a32f4424fde36a = L.marker(
                [2.78, 125.48],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_65ee50459c5365b2f9c16627972f4c70 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_988d8f97f7f46f7011a32f4424fde36a.setIcon(icon_65ee50459c5365b2f9c16627972f4c70);


        var popup_84264fb236aa8701adeca9af2db0eaa0 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_1218ad42fa7881e9a141c2021eb2dc90 = $(`&lt;div id=&quot;html_1218ad42fa7881e9a141c2021eb2dc90&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Karangetang [Api Siau]&lt;/div&gt;`)[0];
            popup_84264fb236aa8701adeca9af2db0eaa0.setContent(html_1218ad42fa7881e9a141c2021eb2dc90);


        marker_988d8f97f7f46f7011a32f4424fde36a.bindPopup(popup_84264fb236aa8701adeca9af2db0eaa0)
        ;




            var marker_06717509c74b93f9481998ad437498db = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_802466892b86cd852b69bf3ed2c7ccfc = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_06717509c74b93f9481998ad437498db.setIcon(icon_802466892b86cd852b69bf3ed2c7ccfc);


        var popup_0543b190ce2f29b7bb3afe5890478c69 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_1e0a394f02954505474dd248d6486119 = $(`&lt;div id=&quot;html_1e0a394f02954505474dd248d6486119&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_0543b190ce2f29b7bb3afe5890478c69.setContent(html_1e0a394f02954505474dd248d6486119);


        marker_06717509c74b93f9481998ad437498db.bindPopup(popup_0543b190ce2f29b7bb3afe5890478c69)
        ;




            var marker_0d7b67ccdf9dd2cdb7aaf81667252487 = L.marker(
                [-7.542, 110.442],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_00b86889f93a6384d7a6502e31f2ea4c = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_0d7b67ccdf9dd2cdb7aaf81667252487.setIcon(icon_00b86889f93a6384d7a6502e31f2ea4c);


        var popup_5f5bef590fa343c81b91ac76507f3158 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_f9de6ab3c54c5727c0152125ab0171ca = $(`&lt;div id=&quot;html_f9de6ab3c54c5727c0152125ab0171ca&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Merapi&lt;/div&gt;`)[0];
            popup_5f5bef590fa343c81b91ac76507f3158.setContent(html_f9de6ab3c54c5727c0152125ab0171ca);


        marker_0d7b67ccdf9dd2cdb7aaf81667252487.bindPopup(popup_5f5bef590fa343c81b91ac76507f3158)
        ;




            var marker_50f72117cddbfa53a40a717ae31e771b = L.marker(
                [-1.467, -78.442],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_e9c27ed899e8640d6093e2bacedf22b1 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_50f72117cddbfa53a40a717ae31e771b.setIcon(icon_e9c27ed899e8640d6093e2bacedf22b1);


        var popup_af682b68296c16d492aed21cc77a5c21 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_4f432ef4616554b688c3b0a377b3f18a = $(`&lt;div id=&quot;html_4f432ef4616554b688c3b0a377b3f18a&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Tungurahua&lt;/div&gt;`)[0];
            popup_af682b68296c16d492aed21cc77a5c21.setContent(html_4f432ef4616554b688c3b0a377b3f18a);


        marker_50f72117cddbfa53a40a717ae31e771b.bindPopup(popup_af682b68296c16d492aed21cc77a5c21)
        ;




            var marker_45eb00c89709a01c6f9554abc13f0ab7 = L.marker(
                [-7.942, 112.95],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_ced20d9bcd265b69bce10a4ee9c514fa = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_45eb00c89709a01c6f9554abc13f0ab7.setIcon(icon_ced20d9bcd265b69bce10a4ee9c514fa);


        var popup_a98300aefb92b1cca1b97a651ddca3d0 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_ed2df27ed8123d271f8c6bc66ae62fa8 = $(`&lt;div id=&quot;html_ed2df27ed8123d271f8c6bc66ae62fa8&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Tengger Caldera&lt;/div&gt;`)[0];
            popup_a98300aefb92b1cca1b97a651ddca3d0.setContent(html_ed2df27ed8123d271f8c6bc66ae62fa8);


        marker_45eb00c89709a01c6f9554abc13f0ab7.bindPopup(popup_a98300aefb92b1cca1b97a651ddca3d0)
        ;




            var marker_59012427fcea7390aacb3039aa7add8e = L.marker(
                [-7.542, 110.442],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_8a01ab15971e9cd0e3701f9ab029362b = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_59012427fcea7390aacb3039aa7add8e.setIcon(icon_8a01ab15971e9cd0e3701f9ab029362b);


        var popup_2942226a4dfc4d946cae0a749cd5fbd8 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_993887157bcd3ede8b7c677ac974508e = $(`&lt;div id=&quot;html_993887157bcd3ede8b7c677ac974508e&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Merapi&lt;/div&gt;`)[0];
            popup_2942226a4dfc4d946cae0a749cd5fbd8.setContent(html_993887157bcd3ede8b7c677ac974508e);


        marker_59012427fcea7390aacb3039aa7add8e.bindPopup(popup_2942226a4dfc4d946cae0a749cd5fbd8)
        ;




            var marker_dcfd9dc4588c3dd8104ede30592e5130 = L.marker(
                [31.93, 130.87],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_7d49fe3cc586332bb1a2415bf99be6b1 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_dcfd9dc4588c3dd8104ede30592e5130.setIcon(icon_7d49fe3cc586332bb1a2415bf99be6b1);


        var popup_c6e297441a65939f1d6d0472c04bef23 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_3af3bcd751a84b38d5e58d9c8e08e576 = $(`&lt;div id=&quot;html_3af3bcd751a84b38d5e58d9c8e08e576&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kirishima&lt;/div&gt;`)[0];
            popup_c6e297441a65939f1d6d0472c04bef23.setContent(html_3af3bcd751a84b38d5e58d9c8e08e576);


        marker_dcfd9dc4588c3dd8104ede30592e5130.bindPopup(popup_c6e297441a65939f1d6d0472c04bef23)
        ;




            var marker_d5ff2a0c47863995c0ce751c6e5db4f1 = L.marker(
                [12.77, 124.05],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_508d9622f53a22d631ef81cc54aff989 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_d5ff2a0c47863995c0ce751c6e5db4f1.setIcon(icon_508d9622f53a22d631ef81cc54aff989);


        var popup_d9be64d96872aba09f07d6f9d6368b78 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_ab5b170ef40fd240e93166809ccf87e0 = $(`&lt;div id=&quot;html_ab5b170ef40fd240e93166809ccf87e0&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Bulusan&lt;/div&gt;`)[0];
            popup_d9be64d96872aba09f07d6f9d6368b78.setContent(html_ab5b170ef40fd240e93166809ccf87e0);


        marker_d5ff2a0c47863995c0ce751c6e5db4f1.bindPopup(popup_d9be64d96872aba09f07d6f9d6368b78)
        ;




            var marker_ad10f6e05ddf29a2e7532ce4c1ad2529 = L.marker(
                [2.78, 125.48],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_09adc4a5055a3fdc80b47c9ae39bcd5c = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_ad10f6e05ddf29a2e7532ce4c1ad2529.setIcon(icon_09adc4a5055a3fdc80b47c9ae39bcd5c);


        var popup_2bf712f3021e11e91ac538dcfb71bcfb = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_855221867af9d03a0c94a96e64fcdaca = $(`&lt;div id=&quot;html_855221867af9d03a0c94a96e64fcdaca&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Karangetang [Api Siau]&lt;/div&gt;`)[0];
            popup_2bf712f3021e11e91ac538dcfb71bcfb.setContent(html_855221867af9d03a0c94a96e64fcdaca);


        marker_ad10f6e05ddf29a2e7532ce4c1ad2529.bindPopup(popup_2bf712f3021e11e91ac538dcfb71bcfb)
        ;




            var marker_dce8ae8f4f97b0cf4ee93bdc4c23719e = L.marker(
                [-1.467, -78.442],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_40f8a984c15ef9517e952c29b7f0fbda = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_dce8ae8f4f97b0cf4ee93bdc4c23719e.setIcon(icon_40f8a984c15ef9517e952c29b7f0fbda);


        var popup_cca89964cb2d9248db5de97e750cdcc1 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_07581bb86b248d5e0266ec3fdc03ce4e = $(`&lt;div id=&quot;html_07581bb86b248d5e0266ec3fdc03ce4e&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Tungurahua&lt;/div&gt;`)[0];
            popup_cca89964cb2d9248db5de97e750cdcc1.setContent(html_07581bb86b248d5e0266ec3fdc03ce4e);


        marker_dce8ae8f4f97b0cf4ee93bdc4c23719e.bindPopup(popup_cca89964cb2d9248db5de97e750cdcc1)
        ;




            var marker_9a48f9225ea959ae5dae19e21e13a6f2 = L.marker(
                [-40.59, -72.117],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_a1fd23dd53e41eef0651f0134068f36c = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_9a48f9225ea959ae5dae19e21e13a6f2.setIcon(icon_a1fd23dd53e41eef0651f0134068f36c);


        var popup_2f9858db2dcf232de90522ef1f3aa2f4 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_0a0aa440d600193776941bb3bd1f84ef = $(`&lt;div id=&quot;html_0a0aa440d600193776941bb3bd1f84ef&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Puyehue&lt;/div&gt;`)[0];
            popup_2f9858db2dcf232de90522ef1f3aa2f4.setContent(html_0a0aa440d600193776941bb3bd1f84ef);


        marker_9a48f9225ea959ae5dae19e21e13a6f2.bindPopup(popup_2f9858db2dcf232de90522ef1f3aa2f4)
        ;




            var marker_f02458a042775453b3269d97def88ad9 = L.marker(
                [13.37, 41.7],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_4a1f44b8ba8cb6d541f959aae9affc4b = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_f02458a042775453b3269d97def88ad9.setIcon(icon_4a1f44b8ba8cb6d541f959aae9affc4b);


        var popup_ae34fc2274e303778ff8bd05797028c7 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_14e81e1584d1f00083b03befecdc7f05 = $(`&lt;div id=&quot;html_14e81e1584d1f00083b03befecdc7f05&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Nabro&lt;/div&gt;`)[0];
            popup_ae34fc2274e303778ff8bd05797028c7.setContent(html_14e81e1584d1f00083b03befecdc7f05);


        marker_f02458a042775453b3269d97def88ad9.bindPopup(popup_ae34fc2274e303778ff8bd05797028c7)
        ;




            var marker_502a90ebd30b987143ddb3f5c7977dfd = L.marker(
                [63.63, -19.05],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_75462124f1356dad272fcbb6eb4efaee = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_502a90ebd30b987143ddb3f5c7977dfd.setIcon(icon_75462124f1356dad272fcbb6eb4efaee);


        var popup_30f3cc6d1fac407b63076e1ffccb44bb = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_24119ae23eb43a9866d279bb6c3442f4 = $(`&lt;div id=&quot;html_24119ae23eb43a9866d279bb6c3442f4&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Katla&lt;/div&gt;`)[0];
            popup_30f3cc6d1fac407b63076e1ffccb44bb.setContent(html_24119ae23eb43a9866d279bb6c3442f4);


        marker_502a90ebd30b987143ddb3f5c7977dfd.bindPopup(popup_30f3cc6d1fac407b63076e1ffccb44bb)
        ;




            var marker_4cac334f6b8bc422067a89f26f8c2f96 = L.marker(
                [1.358, 124.792],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_9362ba3ed6a75fedb273b7594479ff15 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_4cac334f6b8bc422067a89f26f8c2f96.setIcon(icon_9362ba3ed6a75fedb273b7594479ff15);


        var popup_1653f142baceab9edca06af4c82f9d6e = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_0b81912c009f8e0f56533c2a45d4c857 = $(`&lt;div id=&quot;html_0b81912c009f8e0f56533c2a45d4c857&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Lokon-Empung&lt;/div&gt;`)[0];
            popup_1653f142baceab9edca06af4c82f9d6e.setContent(html_0b81912c009f8e0f56533c2a45d4c857);


        marker_4cac334f6b8bc422067a89f26f8c2f96.bindPopup(popup_1653f142baceab9edca06af4c82f9d6e)
        ;




            var marker_4de61c028f6652f9f2e07b4fb047e503 = L.marker(
                [0.8, 127.325],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_29e481847f86f3b94fa29ad38453ddd7 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_4de61c028f6652f9f2e07b4fb047e503.setIcon(icon_29e481847f86f3b94fa29ad38453ddd7);


        var popup_34d54236c54b263534979bc8621cce5e = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_df15382ea9e787e961d0480caf256a6c = $(`&lt;div id=&quot;html_df15382ea9e787e961d0480caf256a6c&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Gamalama&lt;/div&gt;`)[0];
            popup_34d54236c54b263534979bc8621cce5e.setContent(html_df15382ea9e787e961d0480caf256a6c);


        marker_4de61c028f6652f9f2e07b4fb047e503.bindPopup(popup_34d54236c54b263534979bc8621cce5e)
        ;




            var marker_c0d2c02c95b9bfc6d1d6a3491509652c = L.marker(
                [19.425, -155.292],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_fd48f4adca90cd1ccb4f21b3b03e9432 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_c0d2c02c95b9bfc6d1d6a3491509652c.setIcon(icon_fd48f4adca90cd1ccb4f21b3b03e9432);


        var popup_f1ae1793a2d77a6cb105b885815d34c0 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_2205189e855cb5603bcefbf16f2ccf54 = $(`&lt;div id=&quot;html_2205189e855cb5603bcefbf16f2ccf54&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kilauea&lt;/div&gt;`)[0];
            popup_f1ae1793a2d77a6cb105b885815d34c0.setContent(html_2205189e855cb5603bcefbf16f2ccf54);


        marker_c0d2c02c95b9bfc6d1d6a3491509652c.bindPopup(popup_f1ae1793a2d77a6cb105b885815d34c0)
        ;




            var marker_754b28309f574fc6df683978c2b92d49 = L.marker(
                [19.425, -155.292],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_97d259143cca2e3663afb51e105f16ec = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_754b28309f574fc6df683978c2b92d49.setIcon(icon_97d259143cca2e3663afb51e105f16ec);


        var popup_1bd5a6049b1b2090adcfcfb66e859032 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_4673809f70536fae348404f68f85d1a2 = $(`&lt;div id=&quot;html_4673809f70536fae348404f68f85d1a2&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kilauea&lt;/div&gt;`)[0];
            popup_1bd5a6049b1b2090adcfcfb66e859032.setContent(html_4673809f70536fae348404f68f85d1a2);


        marker_754b28309f574fc6df683978c2b92d49.bindPopup(popup_1bd5a6049b1b2090adcfcfb66e859032)
        ;




            var marker_4b51346a224c7b64cc089814c3f4ab8e = L.marker(
                [55.83, 160.33],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_9f369302fcd9b2d51d701e77603e87ab = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_4b51346a224c7b64cc089814c3f4ab8e.setIcon(icon_9f369302fcd9b2d51d701e77603e87ab);


        var popup_4f23d36bc298305eab6e9eeb6c843dec = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_28bb99bd9507747292edfa00b53380dd = $(`&lt;div id=&quot;html_28bb99bd9507747292edfa00b53380dd&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Tolbachik&lt;/div&gt;`)[0];
            popup_4f23d36bc298305eab6e9eeb6c843dec.setContent(html_28bb99bd9507747292edfa00b53380dd);


        marker_4b51346a224c7b64cc089814c3f4ab8e.bindPopup(popup_4f23d36bc298305eab6e9eeb6c843dec)
        ;




            var marker_b93d4ab3687bd0091df7fd11b595c798 = L.marker(
                [-7.542, 110.442],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_184608d1e33f067e9f1304aba1cffbcb = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_b93d4ab3687bd0091df7fd11b595c798.setIcon(icon_184608d1e33f067e9f1304aba1cffbcb);


        var popup_15afb3c30d1baa422f3d24666d8b9ece = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_bd4eecb38d4c83d3d25b384b65842309 = $(`&lt;div id=&quot;html_bd4eecb38d4c83d3d25b384b65842309&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Merapi&lt;/div&gt;`)[0];
            popup_15afb3c30d1baa422f3d24666d8b9ece.setContent(html_bd4eecb38d4c83d3d25b384b65842309);


        marker_b93d4ab3687bd0091df7fd11b595c798.bindPopup(popup_15afb3c30d1baa422f3d24666d8b9ece)
        ;




            var marker_7d16edecc3494099186d76ae76ef5fc4 = L.marker(
                [-8.32, 121.708],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_20547a2cffbf620b39c3090ef7408a7f = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_7d16edecc3494099186d76ae76ef5fc4.setIcon(icon_20547a2cffbf620b39c3090ef7408a7f);


        var popup_0c74cda2f4a30514c1fe6d18af3bcb8c = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_ec44c9d111c3c761150631a01c91b7a9 = $(`&lt;div id=&quot;html_ec44c9d111c3c761150631a01c91b7a9&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Paluweh&lt;/div&gt;`)[0];
            popup_0c74cda2f4a30514c1fe6d18af3bcb8c.setContent(html_ec44c9d111c3c761150631a01c91b7a9);


        marker_7d16edecc3494099186d76ae76ef5fc4.bindPopup(popup_0c74cda2f4a30514c1fe6d18af3bcb8c)
        ;




            var marker_a0ddfff05fba27c9ab972616dcc0cc6a = L.marker(
                [13.257, 123.685],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_c9b9b6510a864bea8da6d07cb887459a = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_a0ddfff05fba27c9ab972616dcc0cc6a.setIcon(icon_c9b9b6510a864bea8da6d07cb887459a);


        var popup_3d0630372edc2e5201d52a8fc07e2810 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_497338138ad9b475167bdd8ba136aed5 = $(`&lt;div id=&quot;html_497338138ad9b475167bdd8ba136aed5&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Mayon&lt;/div&gt;`)[0];
            popup_3d0630372edc2e5201d52a8fc07e2810.setContent(html_497338138ad9b475167bdd8ba136aed5);


        marker_a0ddfff05fba27c9ab972616dcc0cc6a.bindPopup(popup_3d0630372edc2e5201d52a8fc07e2810)
        ;




            var marker_360d8474cc9bd4b3d345adb86aa05193 = L.marker(
                [-8.32, 121.708],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_79d668e716723f205781767490493ff2 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_360d8474cc9bd4b3d345adb86aa05193.setIcon(icon_79d668e716723f205781767490493ff2);


        var popup_e6b7b9b5db66802b174301b177f84aab = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_3d85720f9dfee1925fed48e3640f909b = $(`&lt;div id=&quot;html_3d85720f9dfee1925fed48e3640f909b&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Paluweh&lt;/div&gt;`)[0];
            popup_e6b7b9b5db66802b174301b177f84aab.setContent(html_3d85720f9dfee1925fed48e3640f909b);


        marker_360d8474cc9bd4b3d345adb86aa05193.bindPopup(popup_e6b7b9b5db66802b174301b177f84aab)
        ;




            var marker_1eb3391d34f174f9c9eecc1c4ebe4e99 = L.marker(
                [-16.355, -70.903],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_7895df91c73d1a2d1373f859530441ae = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_1eb3391d34f174f9c9eecc1c4ebe4e99.setIcon(icon_7895df91c73d1a2d1373f859530441ae);


        var popup_0cd44202ea778c4af2634800a205bba0 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_9ccb5a43a5b7f96b404e11c6c7072066 = $(`&lt;div id=&quot;html_9ccb5a43a5b7f96b404e11c6c7072066&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Ubinas&lt;/div&gt;`)[0];
            popup_0cd44202ea778c4af2634800a205bba0.setContent(html_9ccb5a43a5b7f96b404e11c6c7072066);


        marker_1eb3391d34f174f9c9eecc1c4ebe4e99.bindPopup(popup_0cd44202ea778c4af2634800a205bba0)
        ;




            var marker_36099d7ae1aabe27af41c974bd5d1dc6 = L.marker(
                [31.58, 130.67],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_7ecf10492d7058952a4a0ae2f0afc010 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_36099d7ae1aabe27af41c974bd5d1dc6.setIcon(icon_7ecf10492d7058952a4a0ae2f0afc010);


        var popup_415aede88fd441f8b27fb67bd3698035 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_be7c035eabf7df703bc4d785c0e4812a = $(`&lt;div id=&quot;html_be7c035eabf7df703bc4d785c0e4812a&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sakura-jima&lt;/div&gt;`)[0];
            popup_415aede88fd441f8b27fb67bd3698035.setContent(html_be7c035eabf7df703bc4d785c0e4812a);


        marker_36099d7ae1aabe27af41c974bd5d1dc6.bindPopup(popup_415aede88fd441f8b27fb67bd3698035)
        ;




            var marker_8ad74a618793f543d3e747e1a4e7b7f9 = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_127d611ea81b2b63d37e60a259736950 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_8ad74a618793f543d3e747e1a4e7b7f9.setIcon(icon_127d611ea81b2b63d37e60a259736950);


        var popup_2f59221a97d53e6c26f66f47f1708dc7 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_2e4cc1fe6ccdc1da197ca7007d8c6262 = $(`&lt;div id=&quot;html_2e4cc1fe6ccdc1da197ca7007d8c6262&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_2f59221a97d53e6c26f66f47f1708dc7.setContent(html_2e4cc1fe6ccdc1da197ca7007d8c6262);


        marker_8ad74a618793f543d3e747e1a4e7b7f9.bindPopup(popup_2f59221a97d53e6c26f66f47f1708dc7)
        ;




            var marker_8d51c4b05b005c8f5da48e0bad141f41 = L.marker(
                [-38.12, 176.5],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_8e5ad4c2e9b062ab7da2780144f9db62 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_8d51c4b05b005c8f5da48e0bad141f41.setIcon(icon_8e5ad4c2e9b062ab7da2780144f9db62);


        var popup_cd5a3c34d9f778fc377a8d40f9e97504 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_f06861ca6b6b4de6a046e4e5ca0dc86d = $(`&lt;div id=&quot;html_f06861ca6b6b4de6a046e4e5ca0dc86d&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Okataina&lt;/div&gt;`)[0];
            popup_cd5a3c34d9f778fc377a8d40f9e97504.setContent(html_f06861ca6b6b4de6a046e4e5ca0dc86d);


        marker_8d51c4b05b005c8f5da48e0bad141f41.bindPopup(popup_cd5a3c34d9f778fc377a8d40f9e97504)
        ;




            var marker_afe22387b6047d867e9697c27e339ccb = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_32c1ba45b12ba9e0e9281ad8bbfb7739 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_afe22387b6047d867e9697c27e339ccb.setIcon(icon_32c1ba45b12ba9e0e9281ad8bbfb7739);


        var popup_313d40e4c076cd402cd05098a92ece9e = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_7d4fba94d429dc6890ef2bacda6dde4f = $(`&lt;div id=&quot;html_7d4fba94d429dc6890ef2bacda6dde4f&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_313d40e4c076cd402cd05098a92ece9e.setContent(html_7d4fba94d429dc6890ef2bacda6dde4f);


        marker_afe22387b6047d867e9697c27e339ccb.bindPopup(popup_313d40e4c076cd402cd05098a92ece9e)
        ;




            var marker_89b917941163ce83d03bf3af7c5b3f6d = L.marker(
                [-7.93, 112.308],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_b51805b6d00594e73680c07ed93a82a2 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_89b917941163ce83d03bf3af7c5b3f6d.setIcon(icon_b51805b6d00594e73680c07ed93a82a2);


        var popup_56fd7c86ec01d1a3ba20caa9cfe58398 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_95cbf82c620da3d18aaac2dca6edef60 = $(`&lt;div id=&quot;html_95cbf82c620da3d18aaac2dca6edef60&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kelut&lt;/div&gt;`)[0];
            popup_56fd7c86ec01d1a3ba20caa9cfe58398.setContent(html_95cbf82c620da3d18aaac2dca6edef60);


        marker_89b917941163ce83d03bf3af7c5b3f6d.bindPopup(popup_56fd7c86ec01d1a3ba20caa9cfe58398)
        ;




            var marker_6e8dc6050c632308d7b95873123d5f80 = L.marker(
                [35.9, 137.48],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_6bc192bb0e2ddff4e40df5429f6ae5ff = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_6e8dc6050c632308d7b95873123d5f80.setIcon(icon_6bc192bb0e2ddff4e40df5429f6ae5ff);


        var popup_204e381cfdb5f9b22bf49adfcb78afb8 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_6880242caffbd50cccb4ebaf6580be7d = $(`&lt;div id=&quot;html_6880242caffbd50cccb4ebaf6580be7d&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;On-take&lt;/div&gt;`)[0];
            popup_204e381cfdb5f9b22bf49adfcb78afb8.setContent(html_6880242caffbd50cccb4ebaf6580be7d);


        marker_6e8dc6050c632308d7b95873123d5f80.bindPopup(popup_204e381cfdb5f9b22bf49adfcb78afb8)
        ;




            var marker_6bb3e10681728a4233a9586b79e8cd58 = L.marker(
                [19.425, -155.292],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_08c2eaae2962c6711882b69a7efe1ff0 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_6bb3e10681728a4233a9586b79e8cd58.setIcon(icon_08c2eaae2962c6711882b69a7efe1ff0);


        var popup_2949d97b65b3a496955d441bb724a6a3 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_b4c22c50519e9e89a2da189a92625784 = $(`&lt;div id=&quot;html_b4c22c50519e9e89a2da189a92625784&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kilauea&lt;/div&gt;`)[0];
            popup_2949d97b65b3a496955d441bb724a6a3.setContent(html_b4c22c50519e9e89a2da189a92625784);


        marker_6bb3e10681728a4233a9586b79e8cd58.bindPopup(popup_2949d97b65b3a496955d441bb724a6a3)
        ;




            var marker_c428ddf81dce61bb1a32c8de70789d35 = L.marker(
                [14.95, -24.35],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_308cca0881e7f8bddaa6967a56f4799a = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_c428ddf81dce61bb1a32c8de70789d35.setIcon(icon_308cca0881e7f8bddaa6967a56f4799a);


        var popup_2cc6d2878e4def92d6e1952c7db8bf47 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_c8cf2b4b45c240439fcb0e18cb0f184d = $(`&lt;div id=&quot;html_c8cf2b4b45c240439fcb0e18cb0f184d&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Fogo&lt;/div&gt;`)[0];
            popup_2cc6d2878e4def92d6e1952c7db8bf47.setContent(html_c8cf2b4b45c240439fcb0e18cb0f184d);


        marker_c428ddf81dce61bb1a32c8de70789d35.bindPopup(popup_2cc6d2878e4def92d6e1952c7db8bf47)
        ;




            var marker_49f7a48ae2e43c09af5ef43c36ab57b2 = L.marker(
                [0.8, 127.325],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_d8a78db029effed441ab39eee872db77 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_49f7a48ae2e43c09af5ef43c36ab57b2.setIcon(icon_d8a78db029effed441ab39eee872db77);


        var popup_3e74c4b326561c874e6ff24815dbb70c = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_03602e8162372966177fbdfeb94bfd9c = $(`&lt;div id=&quot;html_03602e8162372966177fbdfeb94bfd9c&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Gamalama&lt;/div&gt;`)[0];
            popup_3e74c4b326561c874e6ff24815dbb70c.setContent(html_03602e8162372966177fbdfeb94bfd9c);


        marker_49f7a48ae2e43c09af5ef43c36ab57b2.bindPopup(popup_3e74c4b326561c874e6ff24815dbb70c)
        ;




            var marker_a590106fa27a759d20abfb04f994d343 = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_df020f45eee6ffa58ace1b0e8a7c1e34 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_a590106fa27a759d20abfb04f994d343.setIcon(icon_df020f45eee6ffa58ace1b0e8a7c1e34);


        var popup_06a87df56f62046dd38c0dda2f194476 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_f6dc963d753105fbcb9646159bb37cd9 = $(`&lt;div id=&quot;html_f6dc963d753105fbcb9646159bb37cd9&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_06a87df56f62046dd38c0dda2f194476.setContent(html_f6dc963d753105fbcb9646159bb37cd9);


        marker_a590106fa27a759d20abfb04f994d343.bindPopup(popup_06a87df56f62046dd38c0dda2f194476)
        ;




            var marker_c6364bf7ce2fc679c83c14d523923b8e = L.marker(
                [-41.326, -72.614],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_7e592fc81df85af1ce288337ef780a84 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_c6364bf7ce2fc679c83c14d523923b8e.setIcon(icon_7e592fc81df85af1ce288337ef780a84);


        var popup_7def03e74c1dfa5f355136e071dae597 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_0d20af3a20b9907e7790cffb0d8361a7 = $(`&lt;div id=&quot;html_0d20af3a20b9907e7790cffb0d8361a7&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Calbuco&lt;/div&gt;`)[0];
            popup_7def03e74c1dfa5f355136e071dae597.setContent(html_0d20af3a20b9907e7790cffb0d8361a7);


        marker_c6364bf7ce2fc679c83c14d523923b8e.bindPopup(popup_7def03e74c1dfa5f355136e071dae597)
        ;




            var marker_bb12c0c103780ecdf2e4069d17ff1203 = L.marker(
                [2.78, 125.48],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_1f0a266b17862da3ec76866a8f3b73cb = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_bb12c0c103780ecdf2e4069d17ff1203.setIcon(icon_1f0a266b17862da3ec76866a8f3b73cb);


        var popup_b458c65c0459a004a13bb0d7ad405cb6 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_cd465ef48e57217a02932e9d3c20215b = $(`&lt;div id=&quot;html_cd465ef48e57217a02932e9d3c20215b&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Karangetang [Api Siau]&lt;/div&gt;`)[0];
            popup_b458c65c0459a004a13bb0d7ad405cb6.setContent(html_cd465ef48e57217a02932e9d3c20215b);


        marker_bb12c0c103780ecdf2e4069d17ff1203.bindPopup(popup_b458c65c0459a004a13bb0d7ad405cb6)
        ;




            var marker_91fe315e457e1205b2433309cf3bf2d8 = L.marker(
                [-4.1, 145.061],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_15bc950456bc36b2982c1e506ee60bba = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_91fe315e457e1205b2433309cf3bf2d8.setIcon(icon_15bc950456bc36b2982c1e506ee60bba);


        var popup_9e8dc1a7d0f6e1ea1eb7333c40b569c8 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_61e6c08821206b00707114d09dc29694 = $(`&lt;div id=&quot;html_61e6c08821206b00707114d09dc29694&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Manam&lt;/div&gt;`)[0];
            popup_9e8dc1a7d0f6e1ea1eb7333c40b569c8.setContent(html_61e6c08821206b00707114d09dc29694);


        marker_91fe315e457e1205b2433309cf3bf2d8.bindPopup(popup_9e8dc1a7d0f6e1ea1eb7333c40b569c8)
        ;




            var marker_3f65a849d0e0c384e2c029f0e6c973b3 = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_b5cf334ca0be9e7103c8eb33b58d07a3 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_3f65a849d0e0c384e2c029f0e6c973b3.setIcon(icon_b5cf334ca0be9e7103c8eb33b58d07a3);


        var popup_0c3805dfbce3872b48835a37ab730293 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_63b285eca8ab91d29365d8776bb05fe0 = $(`&lt;div id=&quot;html_63b285eca8ab91d29365d8776bb05fe0&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_0c3805dfbce3872b48835a37ab730293.setContent(html_63b285eca8ab91d29365d8776bb05fe0);


        marker_3f65a849d0e0c384e2c029f0e6c973b3.bindPopup(popup_0c3805dfbce3872b48835a37ab730293)
        ;




            var marker_7a6f924e594405fd02c046b90c55f640 = L.marker(
                [-38.12, 176.5],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_880979e8d4ccc57ec178030ed6ece1f6 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_7a6f924e594405fd02c046b90c55f640.setIcon(icon_880979e8d4ccc57ec178030ed6ece1f6);


        var popup_0725ddd56efd23970215d63f4e5011d3 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_0872ac1d17c6b6700dcd2ef45f0888ea = $(`&lt;div id=&quot;html_0872ac1d17c6b6700dcd2ef45f0888ea&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Okataina&lt;/div&gt;`)[0];
            popup_0725ddd56efd23970215d63f4e5011d3.setContent(html_0872ac1d17c6b6700dcd2ef45f0888ea);


        marker_7a6f924e594405fd02c046b90c55f640.bindPopup(popup_0725ddd56efd23970215d63f4e5011d3)
        ;




            var marker_9f33a3e4380d8a2e446758adb9fad9a3 = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_e36bfa1cc7d84429dec28afa5bbc56c5 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_9f33a3e4380d8a2e446758adb9fad9a3.setIcon(icon_e36bfa1cc7d84429dec28afa5bbc56c5);


        var popup_14d1c7435a9efdc468214a3334c475cd = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_9cacabe697fd6402502773a762d35d85 = $(`&lt;div id=&quot;html_9cacabe697fd6402502773a762d35d85&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_14d1c7435a9efdc468214a3334c475cd.setContent(html_9cacabe697fd6402502773a762d35d85);


        marker_9f33a3e4380d8a2e446758adb9fad9a3.bindPopup(popup_14d1c7435a9efdc468214a3334c475cd)
        ;




            var marker_79e97c47e5da66588002064c1773a661 = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_e9930302803ca07388019b6cc6bfbf29 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_79e97c47e5da66588002064c1773a661.setIcon(icon_e9930302803ca07388019b6cc6bfbf29);


        var popup_ec0555a7dc6726fdfbb31e502a1b1636 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_2edcf6fbce4d7cd858e74cd9b8d5824f = $(`&lt;div id=&quot;html_2edcf6fbce4d7cd858e74cd9b8d5824f&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_ec0555a7dc6726fdfbb31e502a1b1636.setContent(html_2edcf6fbce4d7cd858e74cd9b8d5824f);


        marker_79e97c47e5da66588002064c1773a661.bindPopup(popup_ec0555a7dc6726fdfbb31e502a1b1636)
        ;




            var marker_6b159a5ebaf3c805851008b778db79d2 = L.marker(
                [44.43, -110.67],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_07b74cffbd2a6300c04776b823cc3304 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_6b159a5ebaf3c805851008b778db79d2.setIcon(icon_07b74cffbd2a6300c04776b823cc3304);


        var popup_e690995a826651f85da0775b41e70eae = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_1c15f67929c960bf16bdd5c1ddf9ef39 = $(`&lt;div id=&quot;html_1c15f67929c960bf16bdd5c1ddf9ef39&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Yellowstone&lt;/div&gt;`)[0];
            popup_e690995a826651f85da0775b41e70eae.setContent(html_1c15f67929c960bf16bdd5c1ddf9ef39);


        marker_6b159a5ebaf3c805851008b778db79d2.bindPopup(popup_e690995a826651f85da0775b41e70eae)
        ;




            var marker_edea1a4f1858b0903eb93846c2235c77 = L.marker(
                [-8.42, 116.47],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_ca740eddfdac908f6501ec8975059fc4 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_edea1a4f1858b0903eb93846c2235c77.setIcon(icon_ca740eddfdac908f6501ec8975059fc4);


        var popup_458d9f48b11232547306c2ae78f9754f = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_064cd07e7fa6dafc1a5f6bb546354130 = $(`&lt;div id=&quot;html_064cd07e7fa6dafc1a5f6bb546354130&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Rinjani&lt;/div&gt;`)[0];
            popup_458d9f48b11232547306c2ae78f9754f.setContent(html_064cd07e7fa6dafc1a5f6bb546354130);


        marker_edea1a4f1858b0903eb93846c2235c77.bindPopup(popup_458d9f48b11232547306c2ae78f9754f)
        ;




            var marker_08de3f562be2371aa20b170c12035c80 = L.marker(
                [32.88, 131.1],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_aadaf34e3ad1a8cd9c2df25c8e00a514 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_08de3f562be2371aa20b170c12035c80.setIcon(icon_aadaf34e3ad1a8cd9c2df25c8e00a514);


        var popup_531ac8075df47ca930eea0e47e1cca4f = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_a4e2b63830323b7c0787466b4292d69f = $(`&lt;div id=&quot;html_a4e2b63830323b7c0787466b4292d69f&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Aso&lt;/div&gt;`)[0];
            popup_531ac8075df47ca930eea0e47e1cca4f.setContent(html_a4e2b63830323b7c0787466b4292d69f);


        marker_08de3f562be2371aa20b170c12035c80.bindPopup(popup_531ac8075df47ca930eea0e47e1cca4f)
        ;




            var marker_d7c0aa403aa02f7f77c2f0363037225a = L.marker(
                [37.734, 15.004],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_14c7fc9719e9448b9e72856860b99e92 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_d7c0aa403aa02f7f77c2f0363037225a.setIcon(icon_14c7fc9719e9448b9e72856860b99e92);


        var popup_85fe574e1ec01cc51c527236da692565 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_2d4340f68b0f8ed5cdd4bd14e0b52514 = $(`&lt;div id=&quot;html_2d4340f68b0f8ed5cdd4bd14e0b52514&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Etna&lt;/div&gt;`)[0];
            popup_85fe574e1ec01cc51c527236da692565.setContent(html_2d4340f68b0f8ed5cdd4bd14e0b52514);


        marker_d7c0aa403aa02f7f77c2f0363037225a.bindPopup(popup_85fe574e1ec01cc51c527236da692565)
        ;




            var marker_ef9e2f998d00483074064ff5cc0a7238 = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_a4398084ecd1a973cbcf8d4cc6968087 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_ef9e2f998d00483074064ff5cc0a7238.setIcon(icon_a4398084ecd1a973cbcf8d4cc6968087);


        var popup_d907769408bdd933e1f0a5358fb932c7 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_5024522ff3c6f7e02b4c4ae4af9735d7 = $(`&lt;div id=&quot;html_5024522ff3c6f7e02b4c4ae4af9735d7&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_d907769408bdd933e1f0a5358fb932c7.setContent(html_5024522ff3c6f7e02b4c4ae4af9735d7);


        marker_ef9e2f998d00483074064ff5cc0a7238.bindPopup(popup_d907769408bdd933e1f0a5358fb932c7)
        ;




            var marker_3292b55b55fc236996f5f5ce1307d0e1 = L.marker(
                [14.473, -90.88],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_6d00b1d1e7e868c97e75313cfbaa4196 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_3292b55b55fc236996f5f5ce1307d0e1.setIcon(icon_6d00b1d1e7e868c97e75313cfbaa4196);


        var popup_2ef69e49eafacb3e99a37eaefc0932ae = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_cb90138e1d7b8bc7b8aa87cfe7647967 = $(`&lt;div id=&quot;html_cb90138e1d7b8bc7b8aa87cfe7647967&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Fuego&lt;/div&gt;`)[0];
            popup_2ef69e49eafacb3e99a37eaefc0932ae.setContent(html_cb90138e1d7b8bc7b8aa87cfe7647967);


        marker_3292b55b55fc236996f5f5ce1307d0e1.bindPopup(popup_2ef69e49eafacb3e99a37eaefc0932ae)
        ;




            var marker_5864fba24d17e0ebe971de37c6a38456 = L.marker(
                [-7.2, 109.92],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_8c0d7311786d2f1dda53998b5237ec6c = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_5864fba24d17e0ebe971de37c6a38456.setIcon(icon_8c0d7311786d2f1dda53998b5237ec6c);


        var popup_5aa9d5ff4b0ad3661b597bff27c0ad11 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_591dbaa6d2c348ba2baca8e3441a513e = $(`&lt;div id=&quot;html_591dbaa6d2c348ba2baca8e3441a513e&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Dieng Volc Complex&lt;/div&gt;`)[0];
            popup_5aa9d5ff4b0ad3661b597bff27c0ad11.setContent(html_591dbaa6d2c348ba2baca8e3441a513e);


        marker_5864fba24d17e0ebe971de37c6a38456.bindPopup(popup_5aa9d5ff4b0ad3661b597bff27c0ad11)
        ;




            var marker_63fd2373222b9a79264da375031e9175 = L.marker(
                [40.827, 14.139],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_f642b8329d5f767b76bf1e0d0a783084 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_63fd2373222b9a79264da375031e9175.setIcon(icon_f642b8329d5f767b76bf1e0d0a783084);


        var popup_384f8e2c350aaf365d0f827fda1b7890 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_54c9af4a1f73f89b31106743b7fc10e4 = $(`&lt;div id=&quot;html_54c9af4a1f73f89b31106743b7fc10e4&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Campi Flegrei&lt;/div&gt;`)[0];
            popup_384f8e2c350aaf365d0f827fda1b7890.setContent(html_54c9af4a1f73f89b31106743b7fc10e4);


        marker_63fd2373222b9a79264da375031e9175.bindPopup(popup_384f8e2c350aaf365d0f827fda1b7890)
        ;




            var marker_cb69e81116c42c52e9c6caba8f5c02b5 = L.marker(
                [-15.4, 167.83],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_e7ccca9ebe1078edd330cb4c186f05e4 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_cb69e81116c42c52e9c6caba8f5c02b5.setIcon(icon_e7ccca9ebe1078edd330cb4c186f05e4);


        var popup_c3662303b770292fca9f54626ee4217a = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_e91969136b53702c21d8b72aea18dbc6 = $(`&lt;div id=&quot;html_e91969136b53702c21d8b72aea18dbc6&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Aoba&lt;/div&gt;`)[0];
            popup_c3662303b770292fca9f54626ee4217a.setContent(html_e91969136b53702c21d8b72aea18dbc6);


        marker_cb69e81116c42c52e9c6caba8f5c02b5.bindPopup(popup_c3662303b770292fca9f54626ee4217a)
        ;




            var marker_947e639e88c5927353b7165828b1c44a = L.marker(
                [-7.542, 110.442],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_adab3a97f39fe58393973d542e3c35b0 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_947e639e88c5927353b7165828b1c44a.setIcon(icon_adab3a97f39fe58393973d542e3c35b0);


        var popup_9cf9c06baaefd117994c2271e4e3f437 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_6a7010a4a4034eefd597654b0f7b3a9a = $(`&lt;div id=&quot;html_6a7010a4a4034eefd597654b0f7b3a9a&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Merapi&lt;/div&gt;`)[0];
            popup_9cf9c06baaefd117994c2271e4e3f437.setContent(html_6a7010a4a4034eefd597654b0f7b3a9a);


        marker_947e639e88c5927353b7165828b1c44a.bindPopup(popup_9cf9c06baaefd117994c2271e4e3f437)
        ;




            var marker_d470cc1e8884c51d4cc6e6c147d4d848 = L.marker(
                [3.17, 98.392],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_dab043a9dcdafafab130c70155021e03 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_d470cc1e8884c51d4cc6e6c147d4d848.setIcon(icon_dab043a9dcdafafab130c70155021e03);


        var popup_c0a16a6c5a43853b4b3e6f67b8007e19 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_2f5b4be2ffc97fddd964b325d436d991 = $(`&lt;div id=&quot;html_2f5b4be2ffc97fddd964b325d436d991&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Sinabung&lt;/div&gt;`)[0];
            popup_c0a16a6c5a43853b4b3e6f67b8007e19.setContent(html_2f5b4be2ffc97fddd964b325d436d991);


        marker_d470cc1e8884c51d4cc6e6c147d4d848.bindPopup(popup_c0a16a6c5a43853b4b3e6f67b8007e19)
        ;




            var marker_e222597fedf8ea811dd463513c2075c5 = L.marker(
                [-3.62, 144.62],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_dc30ca31cf817bf68eee84dcdd6ab232 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_e222597fedf8ea811dd463513c2075c5.setIcon(icon_dc30ca31cf817bf68eee84dcdd6ab232);


        var popup_e4ed826a05570aaffebadda18e51d452 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_4367a81576fa1aeba486a2da1502a699 = $(`&lt;div id=&quot;html_4367a81576fa1aeba486a2da1502a699&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kadovar&lt;/div&gt;`)[0];
            popup_e4ed826a05570aaffebadda18e51d452.setContent(html_4367a81576fa1aeba486a2da1502a699);


        marker_e222597fedf8ea811dd463513c2075c5.bindPopup(popup_e4ed826a05570aaffebadda18e51d452)
        ;




            var marker_bc007395242719cede1cc2fd53792038 = L.marker(
                [13.257, 123.685],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_862911325ab0e8a43ead50916a29c058 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_bc007395242719cede1cc2fd53792038.setIcon(icon_862911325ab0e8a43ead50916a29c058);


        var popup_29093711522d9ccc12755612906ef0b1 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_18dc4d2caae6d554fc7df15bf8f21936 = $(`&lt;div id=&quot;html_18dc4d2caae6d554fc7df15bf8f21936&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Mayon&lt;/div&gt;`)[0];
            popup_29093711522d9ccc12755612906ef0b1.setContent(html_18dc4d2caae6d554fc7df15bf8f21936);


        marker_bc007395242719cede1cc2fd53792038.bindPopup(popup_29093711522d9ccc12755612906ef0b1)
        ;




            var marker_ad1ea9ebfbc93e61fd4e8d54157365c0 = L.marker(
                [36.62, 138.55],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_e2627d5870ae4e7a5ce9754ecb25ae1b = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_ad1ea9ebfbc93e61fd4e8d54157365c0.setIcon(icon_e2627d5870ae4e7a5ce9754ecb25ae1b);


        var popup_e55556ed12e6c32a80ac34e8343efdc1 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_eb5aba6948f08b84b4d816f28a23edc2 = $(`&lt;div id=&quot;html_eb5aba6948f08b84b4d816f28a23edc2&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kusatsu-Shirane&lt;/div&gt;`)[0];
            popup_e55556ed12e6c32a80ac34e8343efdc1.setContent(html_eb5aba6948f08b84b4d816f28a23edc2);


        marker_ad1ea9ebfbc93e61fd4e8d54157365c0.bindPopup(popup_e55556ed12e6c32a80ac34e8343efdc1)
        ;




            var marker_615a25a3015891e6ab53106b9fe9c826 = L.marker(
                [19.425, -155.292],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_b4fe069d58a5ce27265a6e8d7133d3cc = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_615a25a3015891e6ab53106b9fe9c826.setIcon(icon_b4fe069d58a5ce27265a6e8d7133d3cc);


        var popup_46de5042a7e98415444ae5087206f0ac = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_4cb0a6539d2c8b0c224236a935293111 = $(`&lt;div id=&quot;html_4cb0a6539d2c8b0c224236a935293111&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kilauea&lt;/div&gt;`)[0];
            popup_46de5042a7e98415444ae5087206f0ac.setContent(html_4cb0a6539d2c8b0c224236a935293111);


        marker_615a25a3015891e6ab53106b9fe9c826.bindPopup(popup_46de5042a7e98415444ae5087206f0ac)
        ;




            var marker_b249acf00d736e4c692e0b87d98952fe = L.marker(
                [-3.62, 144.62],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_1f757078607520b80338d3f5f09d9d34 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_b249acf00d736e4c692e0b87d98952fe.setIcon(icon_1f757078607520b80338d3f5f09d9d34);


        var popup_1bd753adfaac55e8c2ab5b7f483203e0 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_b642f1538d62807be4c3a0e61c32504f = $(`&lt;div id=&quot;html_b642f1538d62807be4c3a0e61c32504f&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kadovar&lt;/div&gt;`)[0];
            popup_1bd753adfaac55e8c2ab5b7f483203e0.setContent(html_b642f1538d62807be4c3a0e61c32504f);


        marker_b249acf00d736e4c692e0b87d98952fe.bindPopup(popup_1bd753adfaac55e8c2ab5b7f483203e0)
        ;




            var marker_cb31feb9361271a8852a9b85ce6362d4 = L.marker(
                [-8.058, 114.242],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_eb5183135cac090be04be8467c217fac = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_cb31feb9361271a8852a9b85ce6362d4.setIcon(icon_eb5183135cac090be04be8467c217fac);


        var popup_03a927804ad99fbc96b72727edc64dd7 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_41de43a77deec62fecbb16a5623669e0 = $(`&lt;div id=&quot;html_41de43a77deec62fecbb16a5623669e0&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Ijen&lt;/div&gt;`)[0];
            popup_03a927804ad99fbc96b72727edc64dd7.setContent(html_41de43a77deec62fecbb16a5623669e0);


        marker_cb31feb9361271a8852a9b85ce6362d4.bindPopup(popup_03a927804ad99fbc96b72727edc64dd7)
        ;




            var marker_d2bba5640db9e6ffb7a1818f6f5fcfb0 = L.marker(
                [19.425, -155.292],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_3d72946d60b02d9407ab5c04cce42d40 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_d2bba5640db9e6ffb7a1818f6f5fcfb0.setIcon(icon_3d72946d60b02d9407ab5c04cce42d40);


        var popup_598a0d6f526ce508b97283d712927837 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_6d2d714c0d9955408442aef14c199867 = $(`&lt;div id=&quot;html_6d2d714c0d9955408442aef14c199867&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Kilauea&lt;/div&gt;`)[0];
            popup_598a0d6f526ce508b97283d712927837.setContent(html_6d2d714c0d9955408442aef14c199867);


        marker_d2bba5640db9e6ffb7a1818f6f5fcfb0.bindPopup(popup_598a0d6f526ce508b97283d712927837)
        ;




            var marker_4778cd644593b5f2acc6d063652f68f5 = L.marker(
                [-15.4, 167.83],
                {}
            ).addTo(feature_group_bc7dabeecca361cb29368f22f5f10a4c);


            var icon_773c4b34bb6106a5eb76f5088e457f21 = L.AwesomeMarkers.icon(
                {&quot;extraClasses&quot;: &quot;fa-rotate-0&quot;, &quot;icon&quot;: &quot;info-sign&quot;, &quot;iconColor&quot;: &quot;white&quot;, &quot;markerColor&quot;: &quot;blue&quot;, &quot;prefix&quot;: &quot;glyphicon&quot;}
            );
            marker_4778cd644593b5f2acc6d063652f68f5.setIcon(icon_773c4b34bb6106a5eb76f5088e457f21);


        var popup_099fd4595c9b791ef66ad93e054d7540 = L.popup({&quot;maxWidth&quot;: &quot;100%&quot;});


            var html_4b4185a2b21d437a63600c829dd896b1 = $(`&lt;div id=&quot;html_4b4185a2b21d437a63600c829dd896b1&quot; style=&quot;width: 100.0%; height: 100.0%;&quot;&gt;Aoba&lt;/div&gt;`)[0];
            popup_099fd4595c9b791ef66ad93e054d7540.setContent(html_4b4185a2b21d437a63600c829dd896b1);


        marker_4778cd644593b5f2acc6d063652f68f5.bindPopup(popup_099fd4595c9b791ef66ad93e054d7540)
        ;



&lt;/script&gt;" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>




```python

```
