{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "7681f405",
   "metadata": {},
   "outputs": [],
   "source": [
    "import numpy as np\n",
    "import pandas as pd"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "id": "801f1290",
   "metadata": {},
   "outputs": [],
   "source": [
    "df = pd.read_csv(r\"C:\\Users\\nette\\Downloads\\new-york-city-taxi-fare-prediction\\data1.csv\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "id": "a0515a76",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>key</th>\n",
       "      <th>pickup_datetime</th>\n",
       "      <th>pickup_longitude</th>\n",
       "      <th>pickup_latitude</th>\n",
       "      <th>dropoff_longitude</th>\n",
       "      <th>dropoff_latitude</th>\n",
       "      <th>passenger_count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>2015-01-27 13:08:24.0000002</td>\n",
       "      <td>2015-01-27 13:08:24 UTC</td>\n",
       "      <td>-73.973320</td>\n",
       "      <td>40.763805</td>\n",
       "      <td>-73.981430</td>\n",
       "      <td>40.743835</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>2015-01-27 13:08:24.0000003</td>\n",
       "      <td>2015-01-27 13:08:24 UTC</td>\n",
       "      <td>-73.986862</td>\n",
       "      <td>40.719383</td>\n",
       "      <td>-73.998886</td>\n",
       "      <td>40.739201</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2011-10-08 11:53:44.0000002</td>\n",
       "      <td>2011-10-08 11:53:44 UTC</td>\n",
       "      <td>-73.982524</td>\n",
       "      <td>40.751260</td>\n",
       "      <td>-73.979654</td>\n",
       "      <td>40.746139</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>2012-12-01 21:12:12.0000002</td>\n",
       "      <td>2012-12-01 21:12:12 UTC</td>\n",
       "      <td>-73.981160</td>\n",
       "      <td>40.767807</td>\n",
       "      <td>-73.990448</td>\n",
       "      <td>40.751635</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>2012-12-01 21:12:12.0000003</td>\n",
       "      <td>2012-12-01 21:12:12 UTC</td>\n",
       "      <td>-73.966046</td>\n",
       "      <td>40.789775</td>\n",
       "      <td>-73.988565</td>\n",
       "      <td>40.744427</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                           key          pickup_datetime  pickup_longitude  \\\n",
       "0  2015-01-27 13:08:24.0000002  2015-01-27 13:08:24 UTC        -73.973320   \n",
       "1  2015-01-27 13:08:24.0000003  2015-01-27 13:08:24 UTC        -73.986862   \n",
       "2  2011-10-08 11:53:44.0000002  2011-10-08 11:53:44 UTC        -73.982524   \n",
       "3  2012-12-01 21:12:12.0000002  2012-12-01 21:12:12 UTC        -73.981160   \n",
       "4  2012-12-01 21:12:12.0000003  2012-12-01 21:12:12 UTC        -73.966046   \n",
       "\n",
       "   pickup_latitude  dropoff_longitude  dropoff_latitude  passenger_count  \n",
       "0        40.763805         -73.981430         40.743835                1  \n",
       "1        40.719383         -73.998886         40.739201                1  \n",
       "2        40.751260         -73.979654         40.746139                1  \n",
       "3        40.767807         -73.990448         40.751635                1  \n",
       "4        40.789775         -73.988565         40.744427                1  "
      ]
     },
     "execution_count": 27,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.head(5)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "id": "51b57596",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>pickup_longitude</th>\n",
       "      <th>pickup_latitude</th>\n",
       "      <th>dropoff_longitude</th>\n",
       "      <th>dropoff_latitude</th>\n",
       "      <th>passenger_count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>9914.000000</td>\n",
       "      <td>9914.000000</td>\n",
       "      <td>9914.000000</td>\n",
       "      <td>9914.000000</td>\n",
       "      <td>9914.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>-73.974722</td>\n",
       "      <td>40.751041</td>\n",
       "      <td>-73.973657</td>\n",
       "      <td>40.751743</td>\n",
       "      <td>1.671273</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>0.042774</td>\n",
       "      <td>0.033541</td>\n",
       "      <td>0.039072</td>\n",
       "      <td>0.035435</td>\n",
       "      <td>1.278747</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>-74.252193</td>\n",
       "      <td>40.573143</td>\n",
       "      <td>-74.263242</td>\n",
       "      <td>40.568973</td>\n",
       "      <td>1.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>-73.992501</td>\n",
       "      <td>40.736125</td>\n",
       "      <td>-73.991247</td>\n",
       "      <td>40.735254</td>\n",
       "      <td>1.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>-73.982326</td>\n",
       "      <td>40.753051</td>\n",
       "      <td>-73.980015</td>\n",
       "      <td>40.754065</td>\n",
       "      <td>1.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>-73.968013</td>\n",
       "      <td>40.767113</td>\n",
       "      <td>-73.964059</td>\n",
       "      <td>40.768757</td>\n",
       "      <td>2.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>-72.986532</td>\n",
       "      <td>41.709555</td>\n",
       "      <td>-72.990963</td>\n",
       "      <td>41.696683</td>\n",
       "      <td>6.000000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "       pickup_longitude  pickup_latitude  dropoff_longitude  dropoff_latitude  \\\n",
       "count       9914.000000      9914.000000        9914.000000       9914.000000   \n",
       "mean         -73.974722        40.751041         -73.973657         40.751743   \n",
       "std            0.042774         0.033541           0.039072          0.035435   \n",
       "min          -74.252193        40.573143         -74.263242         40.568973   \n",
       "25%          -73.992501        40.736125         -73.991247         40.735254   \n",
       "50%          -73.982326        40.753051         -73.980015         40.754065   \n",
       "75%          -73.968013        40.767113         -73.964059         40.768757   \n",
       "max          -72.986532        41.709555         -72.990963         41.696683   \n",
       "\n",
       "       passenger_count  \n",
       "count      9914.000000  \n",
       "mean          1.671273  \n",
       "std           1.278747  \n",
       "min           1.000000  \n",
       "25%           1.000000  \n",
       "50%           1.000000  \n",
       "75%           2.000000  \n",
       "max           6.000000  "
      ]
     },
     "execution_count": 28,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "id": "5bc820a4",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>key</th>\n",
       "      <th>pickup_datetime</th>\n",
       "      <th>pickup_longitude</th>\n",
       "      <th>pickup_latitude</th>\n",
       "      <th>dropoff_longitude</th>\n",
       "      <th>dropoff_latitude</th>\n",
       "      <th>passenger_count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>9909</th>\n",
       "      <td>2015-05-10 12:37:51.0000002</td>\n",
       "      <td>2015-05-10 12:37:51 UTC</td>\n",
       "      <td>-73.968124</td>\n",
       "      <td>40.796997</td>\n",
       "      <td>-73.955643</td>\n",
       "      <td>40.780388</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9910</th>\n",
       "      <td>2015-01-12 17:05:51.0000001</td>\n",
       "      <td>2015-01-12 17:05:51 UTC</td>\n",
       "      <td>-73.945511</td>\n",
       "      <td>40.803600</td>\n",
       "      <td>-73.960213</td>\n",
       "      <td>40.776371</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9911</th>\n",
       "      <td>2015-04-19 20:44:15.0000001</td>\n",
       "      <td>2015-04-19 20:44:15 UTC</td>\n",
       "      <td>-73.991600</td>\n",
       "      <td>40.726608</td>\n",
       "      <td>-73.789742</td>\n",
       "      <td>40.647011</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9912</th>\n",
       "      <td>2015-01-31 01:05:19.0000005</td>\n",
       "      <td>2015-01-31 01:05:19 UTC</td>\n",
       "      <td>-73.985573</td>\n",
       "      <td>40.735432</td>\n",
       "      <td>-73.939178</td>\n",
       "      <td>40.801731</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9913</th>\n",
       "      <td>2015-01-18 14:06:23.0000006</td>\n",
       "      <td>2015-01-18 14:06:23 UTC</td>\n",
       "      <td>-73.988022</td>\n",
       "      <td>40.754070</td>\n",
       "      <td>-74.000282</td>\n",
       "      <td>40.759220</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                              key          pickup_datetime  pickup_longitude  \\\n",
       "9909  2015-05-10 12:37:51.0000002  2015-05-10 12:37:51 UTC        -73.968124   \n",
       "9910  2015-01-12 17:05:51.0000001  2015-01-12 17:05:51 UTC        -73.945511   \n",
       "9911  2015-04-19 20:44:15.0000001  2015-04-19 20:44:15 UTC        -73.991600   \n",
       "9912  2015-01-31 01:05:19.0000005  2015-01-31 01:05:19 UTC        -73.985573   \n",
       "9913  2015-01-18 14:06:23.0000006  2015-01-18 14:06:23 UTC        -73.988022   \n",
       "\n",
       "      pickup_latitude  dropoff_longitude  dropoff_latitude  passenger_count  \n",
       "9909        40.796997         -73.955643         40.780388                6  \n",
       "9910        40.803600         -73.960213         40.776371                6  \n",
       "9911        40.726608         -73.789742         40.647011                6  \n",
       "9912        40.735432         -73.939178         40.801731                6  \n",
       "9913        40.754070         -74.000282         40.759220                6  "
      ]
     },
     "execution_count": 29,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.tail(5)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "id": "8b464ebb",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "key                  9914\n",
       "pickup_datetime      9914\n",
       "pickup_longitude     9914\n",
       "pickup_latitude      9914\n",
       "dropoff_longitude    9914\n",
       "dropoff_latitude     9914\n",
       "passenger_count      9914\n",
       "dtype: int64"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.count()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "id": "382902c6",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 9914 entries, 0 to 9913\n",
      "Data columns (total 7 columns):\n",
      " #   Column             Non-Null Count  Dtype  \n",
      "---  ------             --------------  -----  \n",
      " 0   key                9914 non-null   object \n",
      " 1   pickup_datetime    9914 non-null   object \n",
      " 2   pickup_longitude   9914 non-null   float64\n",
      " 3   pickup_latitude    9914 non-null   float64\n",
      " 4   dropoff_longitude  9914 non-null   float64\n",
      " 5   dropoff_latitude   9914 non-null   float64\n",
      " 6   passenger_count    9914 non-null   int64  \n",
      "dtypes: float64(4), int64(1), object(2)\n",
      "memory usage: 542.3+ KB\n"
     ]
    }
   ],
   "source": [
    "df.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "id": "82453f82",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "key                  0\n",
       "pickup_datetime      0\n",
       "pickup_longitude     0\n",
       "pickup_latitude      0\n",
       "dropoff_longitude    0\n",
       "dropoff_latitude     0\n",
       "passenger_count      0\n",
       "dtype: int64"
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.isnull().sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "id": "5299fe92",
   "metadata": {},
   "outputs": [],
   "source": [
    "df.drop(['key'], axis=1,inplace=True)\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "id": "a66297bd",
   "metadata": {},
   "outputs": [],
   "source": [
    "df.drop(df[df['pickup_longitude'] == 0].index, axis=0, inplace = True)\n",
    "df.drop(df[df['pickup_latitude'] == 0].index, axis=0, inplace = True)\n",
    "df.drop(df[df['dropoff_longitude'] == 0].index, axis=0, inplace = True)\n",
    "df.drop(df[df['dropoff_latitude'] == 0].index, axis=0, inplace = True)\n",
    "df.drop(df[df['passenger_count'] == 208].index, axis=0, inplace = True)\n",
    "df.drop(df[df['passenger_count'] > 5].index, axis=0, inplace = True)\n",
    "df.drop(df[df['passenger_count'] == 0].index, axis=0, inplace = True)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "id": "14f24c8c",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>key</th>\n",
       "      <th>pickup_datetime</th>\n",
       "      <th>pickup_longitude</th>\n",
       "      <th>pickup_latitude</th>\n",
       "      <th>dropoff_longitude</th>\n",
       "      <th>dropoff_latitude</th>\n",
       "      <th>passenger_count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>2015-01-27 13:08:24.0000002</td>\n",
       "      <td>2015-01-27 13:08:24 UTC</td>\n",
       "      <td>-73.973320</td>\n",
       "      <td>40.763805</td>\n",
       "      <td>-73.981430</td>\n",
       "      <td>40.743835</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>2015-01-27 13:08:24.0000003</td>\n",
       "      <td>2015-01-27 13:08:24 UTC</td>\n",
       "      <td>-73.986862</td>\n",
       "      <td>40.719383</td>\n",
       "      <td>-73.998886</td>\n",
       "      <td>40.739201</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2011-10-08 11:53:44.0000002</td>\n",
       "      <td>2011-10-08 11:53:44 UTC</td>\n",
       "      <td>-73.982524</td>\n",
       "      <td>40.751260</td>\n",
       "      <td>-73.979654</td>\n",
       "      <td>40.746139</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>2012-12-01 21:12:12.0000002</td>\n",
       "      <td>2012-12-01 21:12:12 UTC</td>\n",
       "      <td>-73.981160</td>\n",
       "      <td>40.767807</td>\n",
       "      <td>-73.990448</td>\n",
       "      <td>40.751635</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>2012-12-01 21:12:12.0000003</td>\n",
       "      <td>2012-12-01 21:12:12 UTC</td>\n",
       "      <td>-73.966046</td>\n",
       "      <td>40.789775</td>\n",
       "      <td>-73.988565</td>\n",
       "      <td>40.744427</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9909</th>\n",
       "      <td>2015-05-10 12:37:51.0000002</td>\n",
       "      <td>2015-05-10 12:37:51 UTC</td>\n",
       "      <td>-73.968124</td>\n",
       "      <td>40.796997</td>\n",
       "      <td>-73.955643</td>\n",
       "      <td>40.780388</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9910</th>\n",
       "      <td>2015-01-12 17:05:51.0000001</td>\n",
       "      <td>2015-01-12 17:05:51 UTC</td>\n",
       "      <td>-73.945511</td>\n",
       "      <td>40.803600</td>\n",
       "      <td>-73.960213</td>\n",
       "      <td>40.776371</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9911</th>\n",
       "      <td>2015-04-19 20:44:15.0000001</td>\n",
       "      <td>2015-04-19 20:44:15 UTC</td>\n",
       "      <td>-73.991600</td>\n",
       "      <td>40.726608</td>\n",
       "      <td>-73.789742</td>\n",
       "      <td>40.647011</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9912</th>\n",
       "      <td>2015-01-31 01:05:19.0000005</td>\n",
       "      <td>2015-01-31 01:05:19 UTC</td>\n",
       "      <td>-73.985573</td>\n",
       "      <td>40.735432</td>\n",
       "      <td>-73.939178</td>\n",
       "      <td>40.801731</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9913</th>\n",
       "      <td>2015-01-18 14:06:23.0000006</td>\n",
       "      <td>2015-01-18 14:06:23 UTC</td>\n",
       "      <td>-73.988022</td>\n",
       "      <td>40.754070</td>\n",
       "      <td>-74.000282</td>\n",
       "      <td>40.759220</td>\n",
       "      <td>6</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>9914 rows × 7 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "                              key          pickup_datetime  pickup_longitude  \\\n",
       "0     2015-01-27 13:08:24.0000002  2015-01-27 13:08:24 UTC        -73.973320   \n",
       "1     2015-01-27 13:08:24.0000003  2015-01-27 13:08:24 UTC        -73.986862   \n",
       "2     2011-10-08 11:53:44.0000002  2011-10-08 11:53:44 UTC        -73.982524   \n",
       "3     2012-12-01 21:12:12.0000002  2012-12-01 21:12:12 UTC        -73.981160   \n",
       "4     2012-12-01 21:12:12.0000003  2012-12-01 21:12:12 UTC        -73.966046   \n",
       "...                           ...                      ...               ...   \n",
       "9909  2015-05-10 12:37:51.0000002  2015-05-10 12:37:51 UTC        -73.968124   \n",
       "9910  2015-01-12 17:05:51.0000001  2015-01-12 17:05:51 UTC        -73.945511   \n",
       "9911  2015-04-19 20:44:15.0000001  2015-04-19 20:44:15 UTC        -73.991600   \n",
       "9912  2015-01-31 01:05:19.0000005  2015-01-31 01:05:19 UTC        -73.985573   \n",
       "9913  2015-01-18 14:06:23.0000006  2015-01-18 14:06:23 UTC        -73.988022   \n",
       "\n",
       "      pickup_latitude  dropoff_longitude  dropoff_latitude  passenger_count  \n",
       "0           40.763805         -73.981430         40.743835                1  \n",
       "1           40.719383         -73.998886         40.739201                1  \n",
       "2           40.751260         -73.979654         40.746139                1  \n",
       "3           40.767807         -73.990448         40.751635                1  \n",
       "4           40.789775         -73.988565         40.744427                1  \n",
       "...               ...                ...               ...              ...  \n",
       "9909        40.796997         -73.955643         40.780388                6  \n",
       "9910        40.803600         -73.960213         40.776371                6  \n",
       "9911        40.726608         -73.789742         40.647011                6  \n",
       "9912        40.735432         -73.939178         40.801731                6  \n",
       "9913        40.754070         -74.000282         40.759220                6  \n",
       "\n",
       "[9914 rows x 7 columns]"
      ]
     },
     "execution_count": 30,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "93b47363",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.7"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}